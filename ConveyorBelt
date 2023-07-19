using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ConveyorBelt : MonoBehaviour
{
    [SerializeField]
    private float speed, conveyorSpeed;
    [SerializeField]
    private Vector3 direction;
    [SerializeField]
    private List<GameObject> onBelt;

    private Material material;

    // Start is called before the first frame update
    void Start()
    {
        /* Create an instance of this texture
         * This should only be necessary if the belts are using the same material and are moving different speeds
         */
        material = GetComponent<MeshRenderer>().material;
    }

    // Update is called once per frame
    private void Update()
    {
        // Move the conveyor belt texture to make it look like it's moving
        material.mainTextureOffset += new Vector2(0, 1) * conveyorSpeed * Time.deltaTime;
    }

    // Fixed update for physics
    void FixedUpdate()
    {
        // For every item on the belt, add force to it in the direction given
        for (int i = 0; i <= onBelt.Count - 1; i++)
        {
            onBelt[i].GetComponent<Rigidbody>().AddForce(speed * direction);
        }
    }

    // When something collides with the belt
    private void OnCollisionEnter(Collision collision)
    {
        onBelt.Add(collision.gameObject);
    }

    // When something leaves the belt
    private void OnCollisionExit(Collision collision)
    {
        onBelt.Remove(collision.gameObject);
    }
}
