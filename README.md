# docker-angular-devel
deploy AngularJS app quickly in develepment environment

This docker image serve static files from `/opt/angular/app` and pass requests to `/api/` to a backend server `apiserver:3031`.

## Usage

1. Launch a backend server.

    ```
    docker run --name <backend_server_name> -d <backend_server_image>
    ```

2. Launch this server.

    ```
    docker run --name <frontend_server_name> -v <path_of_angualrjs_project>:/opt/angular --link <backend_server_name>:apiserver -P -d billlee/nginx-angular-devel
    ```

3. Get the server port.

    ```
    docker port <frontend_server_name>
    ```

    You will get something like

    ```
    443/tcp -> 0.0.0.0:49153
    80/tcp -> 0.0.0.0:49154
    ```

    Now you may access the server via `http://127.0.0.1:49154`.
