---
title: Dynamo Calculation Python Codes
---
## Python script for random panels
### Full script (copy to dynamo)
```python
data = IN[0]  
true_type = IN[1]  
false_type = IN[2]  
key = IN[3]  
  
results = [x > key for x in data]  
  
types = [true_type if result else false_type for result in results]  
  
OUT = types
```
### Script explained
#### 1. Define inputs
`IN[num]` represent the inputs on the left. You need to provide all of them. 
```python 
data = IN[0]  # All random numbers.
true_type = IN[1]  # Family type if the value is 'True'.
false_type = IN[2] # Family type if the value is 'False'.
key = IN[3]  # Threshold value used for filtering.
```
#### 2. Value filtering
The `results` is a list of boolean values, such as: `[True, True, False]`
```python
results = [x > key for x in data] 
```
#### 3. Assign types
`if result` means result is 'True'
```python
types = [true_type if result else false_type for result in results]  
```
#### 4. Output
This is standard requirement for Dynamo python. `types` is list of family types.
```python
OUT = types
```
## Python script for calculation
### Full script (copy to dynamo)
```python
import math  
import clr  
clr.AddReference('System.Windows.Forms')  
from System.Windows.Forms import MessageBox  
  
angle_deg = IN[0]  
power_per_m2 = IN[1]  
area_mm2 = IN[2]  
  
area_m2 = area_mm2 * 0.000001  
angle_rad = math.radians(angle_deg)  
  
efficiency_factor = max(0.0, math.cos(angle_rad))    
  
output_power = power_per_m2 * efficiency_factor * area_m2  
MessageBox.Show("Total Output Power:\n{:.2f} kW".format(output_power), "Calculation Done")  
  
OUT = output_power
```
### Script explained
#### 1. Import Statements
```python
import math # Package for common math functions
import clr  # A Dynamo required runtime package
clr.AddReference('System.Windows.Forms')  # Enable GUI for messagebox
from System.Windows.Forms import MessageBox # Fucntion for pop-up messagebox
```
#### 2. Define inputs
```python
angle_deg = IN[0]   # Angle in degrees between the sun direction and the wall's normal vector
power_per_m2 = IN[1]  # User defined power output of the solar panel, kw per m2
area_mm2 = IN[2]  # Total area of all solar panels
```
#### 3. Unit conversion
```python
area_m2 = area_mm2 * 0.000001  
angle_rad = math.radians(angle_deg)  # Convert angle from degrees to radians for trigonometric calculations
```
#### 4. Sun efficiency factor
The `efficiency_factor` represents how effectively sunlight hits the surface, based on the angle between the sun's direction and the surface normal. This is computed using the cosine of the incidence angle (in radians).
- When the sunlight hits the surface perpendicularly (angle = 0°), `cos(0) = 1`, meaning 100% efficiency.
- When the angle increases toward 90°, the cosine decreases toward 0, meaning less effective exposure.
- For angles beyond 90°, `cos(angle)` becomes negative, but we clamp it to `0.0` using `max()` to avoid negative efficiency.
```python
efficiency_factor = max(0.0, math.cos(angle_rad))    
```
#### 5. Message box
Calculate the total power output and display with a message box.
```python
output_power = power_per_m2 * efficiency_factor * area_m2  
MessageBox.Show("Total Output Power:\n{:.2f} kW".format(output_power), "Calculation Done")  
```
This is standard requirement for Dynamo python. 
```python
OUT = output_power
```