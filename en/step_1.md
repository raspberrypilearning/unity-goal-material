This script changes the material of all the parts of the goal when the ball collides with any one of them. It also changes the material of individual ramps as the ball rolls over them. 

You need to create a `Goal` tag and add it to all of the GameObjects than make up the goal.

Add the script to all the GameObjects in the goal. 

--- code ---
---
language: cs
filename: GoalController.cs
line_numbers: true
line_number_start: 1
line_highlights:
---

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class GoalController : MonoBehaviour
{

  void OnCollisionEnter(Collision collision)
  {
      if (collision.gameObject.tag == "Player" && gameObject.tag == "Goal"){
            
            var objects = GameObject.FindGameObjectsWithTag("Goal");
        
            foreach (var obj in objects) {
                obj.GetComponent<Renderer>().sharedMaterial = collision.gameObject.GetComponent<Renderer>().sharedMaterial;
            }         
      }
  }

}

--- /code ---
