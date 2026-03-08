1. Open a terminal and SSH into Delta system
```
ssh login.delta.ncsa.illinois.edu
```

2. Setup a virtual  environment with python 3.11
```
python -m venv venv
source venv/bin/activate
```

3. Install globus-compute-endpoint==3.11 for ease of setup.
```
python3 -m pip install globus-compute-endpoint==3.11
```

4. Get a globus-compute-endpoint with default configuration setup
```
globus-compute-endpoint configure diamond_<userId>
```

Edit the config file to update the display name to something useful: `Delta@NCSA`
```
vi /u/<userId>/.globus_compute/diamond_<userId>/config.yaml
```
```
display_name: Delta@NCSA      # ← make sure to set a human readable name
engine:
  max_workers_per_node: 1
  provider:
    init_blocks: 1
    max_blocks: 1
    min_blocks: 0
    type: LocalProvider
  type: GlobusComputeEngine
```

In vim, use “i” to enter editing mode. Use Esc to stop editing, then use :wq to save and quit.

5. Start the endpoint with:
```
globus-compute-endpoint start diamond_<userId>
```

6. Diamond settings page should show your new endpoint under available endpoints: https://diamondhpc.ai/settings
- Go to the available endpoints tab and add the endpoint.
- Once the endpoint is added, it could take a few minutes for Diamond to discover the partition and account on the machine.

7. Run container on the endpoint.

