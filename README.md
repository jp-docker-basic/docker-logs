# Watching Docker Logs in Real-Time

Understanding the docker logs Command

To watch the logs of a running Docker container in real-time, use the `docker logs` command with the `-f` flag:

```bash
docker logs -f <container_id>
```

- `-f`: Follows the log output and prints new lines as they are added

### Example:

```Bash
docker logs -f my_container
```

This command will display the logs of the container with the ID `my_container` and continuously update as new log lines are generated.

## Additional Options

- `--tail`: Specifies the number of lines to show from the end of the logs.

```Bash
docker logs --tail=100 my_container

```

- `--timestamps`: Adds timestamps to each log line.

```bash
docker logs --timestamps my_container
```

- `--since`: Shows logs since a specific timestamp.

```bash
docker logs --since="2023-11-22T10:00:00" my_container

```
