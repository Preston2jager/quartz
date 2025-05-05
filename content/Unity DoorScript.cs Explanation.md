This guide **is not about learning programming**.  Instead, it explains what the `DoorScript.cs` does in your Unity scene so you can tweak its settings with confidence.
### Full Codes
```c#
using UnityEngine;
using UnityEngine.UI;

public class DoorScript : MonoBehaviour
{
    public Transform leftDoorHinge;
    public Transform rightDoorHinge;
    public float openAngle = 90f;
    public float openSpeed = 2f;
    public GameObject popupText; // Assign in Inspector

    private bool isOpen = false;
    private bool inTriggerZone = false;
    private Transform player;

    void Start()
    {
        if (popupText != null)
            popupText.SetActive(false);
    }

    void Update()
    {
        if (inTriggerZone && Input.GetKeyDown(KeyCode.F))
        {
            isOpen = !isOpen;
            StopAllCoroutines();
            StartCoroutine(RotateDoors(isOpen));
            if (popupText != null)
                popupText.SetActive(false); // Hide text when triggered
        }
    }

    private void OnTriggerEnter(Collider other)
    {
        if (other.CompareTag("Player"))
        {
            inTriggerZone = true;
            player = other.transform;
            if (popupText != null)
                popupText.SetActive(true);
        }
    }

    private void OnTriggerExit(Collider other)
    {
        if (other.CompareTag("Player"))
        {
            inTriggerZone = false;
            player = null;
            if (popupText != null)
                popupText.SetActive(false);
        }
    }

    System.Collections.IEnumerator RotateDoors(bool open)
    {
        float targetAngleLeft, targetAngleRight;
        if (player != null && player.position.z < transform.position.z) // Player in front
        {
            targetAngleLeft = open ? openAngle : 0;
            targetAngleRight = open ? -openAngle : 0;
        }
        else
        {
            targetAngleLeft = open ? -openAngle : 0;
            targetAngleRight = open ? openAngle : 0;
        }
        Quaternion startRotationLeft = leftDoorHinge.localRotation;
        Quaternion endRotationLeft = Quaternion.Euler(0, targetAngleLeft, 0);
        Quaternion startRotationRight = rightDoorHinge.localRotation;
        Quaternion endRotationRight = Quaternion.Euler(0, targetAngleRight, 0);
        float time = 0;
        while (time < 1)
        {
            time += Time.deltaTime * openSpeed;
            leftDoorHinge.localRotation = Quaternion.Lerp(startRotationLeft, endRotationLeft, time);
            rightDoorHinge.localRotation = Quaternion.Lerp(startRotationRight, endRotationRight, time);
            yield return null;
        }
        leftDoorHinge.localRotation = endRotationLeft;
        rightDoorHinge.localRotation = endRotationRight;
    }
}
```
## What This Script Achieves

Think of a supermarket’s automatic door:
1. **It knows when you’re nearby.**  
2. **A prompt tells you which key to press.**  
3. **Both panels swing open the safe way, then shut again when you leave.**
That is exactly what this script re‑creates for any two‑panel door model in Unity.
## Things You Set Up in the Inspector

| Setting | What it represents | Typical value |
|---------|--------------------|---------------|
| **Left Door Hinge** | The point where the *left* door panel pivots. | Drag the left panel’s pivot transform here. |
| **Right Door Hinge** | Same for the *right* panel. | Drag the right panel’s pivot transform. |
| **Open Angle** | How wide the door swings each way. | 90° is a full right‑angle. |
| **Open Speed** | How fast it opens/closes. | 2 = fairly quick, 0.5 = slow. |
| **Popup Text** | A UI prompt such as “Press F to open”. | Drop a Canvas Text object here (optional). |

*No coding required:* you simply assign these references in the Unity Editor.
## The Story of What Happens

### 1. Scene Starts  
The script quietly hides the “Press F” prompt so nothing distracts the player.
### 2. Player Approaches  
- An invisible trigger box around the door senses the player’s collider.  
- The prompt pops up, inviting the player to interact.
### 3. Player Presses **F**  
- The script flips a mental switch: **open** if the door was closed, or **close** if it was already open.  
- Any previous opening/closing animation is cancelled so the door never gets confused.
- The prompt disappears (no need to keep showing it while the action is under way).
### 4. Door Panels Swing  
- Each side rotates smoothly from its current position to the target angle.  
- The script first checks which side of the door the player is on so the panels always swing **away** from the player—just like real life, to avoid bumps.
### 5. Player Walks Away  
- When the player exits the trigger box the prompt hides.  
- The door stays in its last position until someone presses **F** again.
## Common Tweaks 

- **Make the door feel heavier:** set *Open Speed* to a lower number.  
- **Only one panel opens:** assign the same Transform to both hinge slots, or leave one slot empty. 
- **Silent doors:** remove the popup text and rely on player intuition.  
- **Different key:** change “F” to another letter inside the Inspector’s *Key Code* field (if you add one)—or ask your programmer to do it.

