> docker info

```yaml
Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
```



# Check Cgroup Driver:

Run `docker info` to check the `Cgroup Driver` value.

- If it's not cgroupfs, you cannot directly access cgroup files for that container.
Inspect Container Status:

- Use `docker ps` to verify the container is running.

If stopped, start it using 

> docker start <container_id>

- Alternative Methods: If you can't access cgroup files directly, consider using docker stats or a metrics collection tool like Prometheus.

## Methods for Collecting Docker Metrics

### 1. Docker Stats Command

The docker stats command provides a real-time view of resource utilization for containers.

```bash
docker stats <container_id>
```

This command displays CPU, memory, network, and block I/O statistics for the specified container.

### 2. Docker Engine Metrics

Docker exposes a set of metrics through its REST API. Tools like Prometheus can be used to scrape these metrics.

```bash
curl http://localhost:2375/v1.40/containers/container_id/stats

```

### 3. Cgroupfs Metrics

Docker uses cgroups to manage container resources. You can directly read metrics from the cgroupfs filesystem.

```bash
cat /sys/fs/cgroup/memory/docker/<container_id>/memory.usage_bytes
```

### 4. Using a Metrics Collector
To streamline the process and provide additional features, consider using a dedicated metrics collector like:

- `Prometheus`: A popular open-source time-series database and monitoring system.
- `Datadog`: A cloud-based monitoring and analytics platform.
- `New Relic`: A cloud-based application performance monitoring platform.