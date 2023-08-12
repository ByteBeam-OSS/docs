## Docker Swarm API Overview with Examples

### **1. Containers**:

- **List all containers**:
  - Endpoint: `GET /containers/json`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/containers/json | jq
  ```

- **Create a container**:
  - Endpoint: `POST /containers/create`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST -H "Content-Type: application/json" -d '{"Image":"alpine", "Cmd":["echo", "hello world"]}' http://localhost/containers/create | jq
  ```

- **Inspect a container**:
  - Endpoint: `GET /containers/{id}/json`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/containers/{id}/json | jq
  ```

- **List processes running inside a container**:
  - Endpoint: `GET /containers/{id}/top`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/containers/{id}/top | jq
  ```

- **Get logs from a container**:
  - Endpoint: `GET /containers/{id}/logs`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/containers/{id}/logs?stdout=true | jq
  ```

- **Start a container**:
  - Endpoint: `POST /containers/{id}/start`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST http://localhost/containers/{id}/start
  ```

- **Stop a container**:
  - Endpoint: `POST /containers/{id}/stop`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST http://localhost/containers/{id}/stop
  ```

- **Restart a container**:
  - Endpoint: `POST /containers/{id}/restart`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST http://localhost/containers/{id}/restart
  ```

- **Kill a container**:
  - Endpoint: `POST /containers/{id}/kill`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST http://localhost/containers/{id}/kill
  ```

- **Delete a container**:
  - Endpoint: `DELETE /containers/{id}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X DELETE http://localhost/containers/{id}
  ```

### **2. Images**:

- **List images**:
  - Endpoint: `GET /images/json`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/images/json | jq
  ```

- **Inspect an image**:
  - Endpoint: `GET /images/{name}/json`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/images/alpine/json | jq
  ```

- **Pull an image**:
  - Endpoint: `POST /images/create`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST -d 'fromImage=alpine' http://localhost/images/create | jq
  ```

- **Remove an image**:
  - Endpoint: `DELETE /images/{name}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X DELETE http://localhost/images/alpine
  ```

### **3. Nodes (Swarm Specific)**:

- **List nodes**:
  - Endpoint: `GET /nodes`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/nodes | jq
  ```

- **Inspect a node**:
  - Endpoint: `GET /nodes/{id}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/nodes/{id} | jq
  ```

- **Update a node**:
  - Endpoint: `POST /nodes/{id}/update`
  ```bash
  # Must provide version and other details in the request body
  ```

- **Delete a node**:
  - Endpoint: `DELETE /nodes/{id}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X DELETE http://localhost/nodes/{id}
  ```

### **4. Services (Swarm Specific)**:

- **List services**:
  - Endpoint: `GET /services`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/services | jq
  ```

- **Create a service**:
  - Endpoint: `POST /services/create`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST -H "Content-Type: application/json" -d '{"Name":"myservice", "TaskTemplate": {"ContainerSpec": {"Image":"alpine", "Command":["sleep", "3600"]}}}' http://localhost/services/create | jq
  ```

- **Inspect a service**:
  - Endpoint: `GET /services/{id}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/services/{id} | jq
  ```

- **Update a service**:
  - Endpoint: `POST /services/{id}/update`
  ```bash
  # This request needs additional details like the version of the service and the new configuration.
  ```

- **Delete a service**:
  - Endpoint: `DELETE /services/{id}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X DELETE http://localhost/services/{id}
  ```

### **5. Tasks (Swarm Specific)**:

- **List tasks**:
  - Endpoint: `GET /tasks`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/tasks | jq
  ```

- **Inspect a task**:
  - Endpoint: `GET /tasks/{id}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/tasks/{id} | jq
  ```

### **6. Secrets (Swarm Specific)**:

- **List secrets**:
  - Endpoint: `GET /secrets`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/secrets | jq
  ```

- **Create a secret**:
  - Endpoint: `POST /secrets/create`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST -H "Content-Type: application/json" -d '{"Name":"mysecret", "Data":"base64_encoded_data"}' http://localhost/secrets/create | jq
  ```

- **Inspect a secret**:
  - Endpoint: `GET /secrets/{id}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/secrets/{id} | jq
  ```

- **Delete a secret**:
  - Endpoint: `DELETE /secrets/{id}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X DELETE http://localhost/secrets/{id}
  ```

### **7. Configs (Swarm Specific)**:

- **List configs**:
  - Endpoint: `GET /configs`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/configs | jq
  ```

- **Create a config**:
  - Endpoint: `POST /configs/create`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST -H "Content-Type: application/json" -d '{"Name":"myconfig", "Data":"base64_encoded_data"}' http://localhost/configs/create | jq
  ```

- **Inspect a config**:
  - Endpoint: `GET /configs/{id}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/configs/{id} | jq
  ```

- **Delete a config**:
  - Endpoint: `DELETE /configs/{id}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X DELETE http://localhost/configs/{id}
  ```


### **8. Plugins**:

- **List plugins**:
  - Endpoint: `GET /plugins`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/plugins | jq
  ```

- **Inspect a plugin**:
  - Endpoint: `GET /plugins/{name}/json`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/plugins/{name}/json | jq
  ```

- **Install a plugin**:
  - Endpoint: `POST /plugins/pull`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST -H "Content-Type: application/json" -d '{"Name":"plugin_name"}' http://localhost/plugins/pull
  ```

- **Enable a plugin**:
  - Endpoint: `POST /plugins/{name}/enable`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST http://localhost/plugins/{name}/enable
  ```

- **Disable a plugin**:
  - Endpoint: `POST /plugins/{name}/disable`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST http://localhost/plugins/{name}/disable
  ```

- **Remove a plugin**:
  - Endpoint: `DELETE /plugins/{name}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X DELETE http://localhost/plugins/{name}
  ```

### **9. Networks**:

- **List networks**:
  - Endpoint: `GET /networks`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/networks | jq
  ```

- **Inspect a network**:
  - Endpoint: `GET /networks/{id}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/networks/{id} | jq
  ```

- **Create a network**:
  - Endpoint: `POST /networks/create`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST -H "Content-Type: application/json" -d '{"Name":"mynetwork", "Driver":"overlay"}' http://localhost/networks/create | jq
  ```

- **Remove a network**:
  - Endpoint: `DELETE /networks/{id}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X DELETE http://localhost/networks/{id}
  ```

### **10. Volumes**:

- **List volumes**:
  - Endpoint: `GET /volumes`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/volumes | jq
  ```

- **Inspect a volume**:
  - Endpoint: `GET /volumes/{name}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/volumes/{name} | jq
  ```

- **Create a volume**:
  - Endpoint: `POST /volumes/create`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST -H "Content-Type: application/json" -d '{"Name":"myvolume"}' http://localhost/volumes/create | jq
  ```

- **Remove a volume**:
  - Endpoint: `DELETE /volumes/{name}`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X DELETE http://localhost/volumes/{name}
  ```

### **11. System**:

- **Get Docker version**:
  - Endpoint: `GET /version`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/version | jq
  ```

- **Get system information**:
  - Endpoint: `GET /info`
  ```bash
  curl -s --unix-socket /var/run/docker.sock http://localhost/info | jq
  ```

### **12. Exec**:

- **Create exec instance**:
  - Endpoint: `POST /containers/{id}/exec`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST -H "Content-Type: application/json" -d '{"AttachStdin":false, "AttachStdout":true, "AttachStderr":true, "Cmd":["date"]}' http://localhost/containers/{id}/exec | jq
  ```

- **Start exec instance**:
  - Endpoint: `POST /exec/{id}/start`
  ```bash
  curl -s --unix-socket /var/run/docker.sock -X POST -H "Content-Type: application/json" -d '{"Detach": false, "Tty": false}' http://localhost/exec/{id}/start | jq
  ```


