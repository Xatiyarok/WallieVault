**Command details**

- `gcloud compute` allows you to manage your Compute Engine resources in a format that's simpler than the Compute Engine API.
- `instances create` creates a new instance.
- `gcelab2` is the name of the VM.
- The `--machine-type` flag specifies the machine type as _e2-medium_.
- The `--zone` flag specifies where the VM is created.
- If you omit the `--zone` flag, the `gcloud` tool can infer your desired zone based on your default properties. Other required instance settings (such as `machine type` and `image`) are set to default values if you do not specify them in the `create` command.