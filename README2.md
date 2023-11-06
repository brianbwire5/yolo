IP 4 

The Yolo-app in our project is set to be managed by Kubernetes, leading to the creation of deployments and services to ensure their operation within the Kubernetes environment. Additionally, our MongoDB databases have been configured correctly.

Deployment to Google Kubernetes Engine

In our application architecture, we have employed StatefulSets for the database and Deployments for the backend.

StatefulSets for the Database:

The application database is ststeless.We have opted for StatefulSets for our database components, as they are well-suited for applications demanding consistent network identities and durable storage. In our specific case, the database qualifies as a stateful application due to its requirement for a consistent network identity to facilitate communication and the need for persistent storage to ensure reliable data storage. Each pod within the StatefulSet is assigned a unique and stable hostname, which guarantees predictable network communication and ensures data persistence, even if a pod is rescheduled or replaced.

Deployments for the Backend :

This is ststeless as well. For our backend services, we have chosen Deployments. Deployments are better suited for stateless applications that can be easily scaled up or down without depending on persistent local storage. In our situation, the backend is considered stateless because it does not rely on locally stored data within the pods. Any necessary data is retrieved from the stateful database. Deployments allow us to horizontally scale, meaning we can dynamically add or remove backend instances based on demand without the need to manage stateful data within each instance.

Both the frontend and backend deployments consist of 3 replicas to ensure redundancy in the event of downtimes or failures.

This architectural decision ensures that our application can benefit from both stable and persistent data storage, as well as the capability to efficiently handle varying workloads.