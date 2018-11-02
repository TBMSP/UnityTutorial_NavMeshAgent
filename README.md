# UnityTutorial_NavMeshAgent
Este es un tutorial de como usar el NavMeshAgent en Unity3D, cuenta con un video publicado en Youtube.

Video de Youtube: https://youtu.be/fBSs9SQPsLo

Paquete con el contenido del tutorial para Unity3D: 

---

### Esta es la clase Player.cs del tutorial:
```c#
using UnityEngine;
using UnityEngine.AI;

public class Player:MonoBehaviour{
  public Transform PuntoCamara,Punto;
  private NavMeshAgent navMeshAgent;
  
  void Start(){
    navMeshAgent=GetComponent<NavMeshAgent>();
  }
  void Update(){
    if(Input.GetMouseButtonDown(0)){
      RaycastHit hit;
      var pos=PuntoCamara.GetChild(0).GetComponent<Camera>().ScreenPointToRay(Input.mousePosition);
      if(Physics.Raycast(pos,out hit,20)){
        navMeshAgent.destination=hit.point;
        Instantiate(Punto,navMeshAgent.destination,Quaternion.identity);
      }
    }
  PuntoCamara.position=Vector3.Lerp(PuntoCamara.position,transform.position,5*Time.deltaTime);
  }
}
```
