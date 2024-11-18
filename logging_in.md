# Logging in to MSI
To connect to an MSI supercomputer, please follow these steps:

### Accept the MSI User Agreement
* You will have received an email invitation to accept the user agreement.
  
### Connect to MSI login node:
* You can SSH to MSI from a terminal with `ssh username@login.msi.umn.edu`
* Alternatively, you can do this using "Open On Demand":
    * Control-click (Windows) or Command-click (Mac) here to open the MSI OnDemand dashboard in a new tab: [https://ood.msi.umn.edu](https://ood.msi.umn.edu)
    * Click Clusters > Agate Shell Access to open a terminal with command-line access to a login node.
    * Click Files > Home Directory to view your files

### Switch to the CSCI 5481 "group" _if_ you also have another group
If you are in a lab group or another class group, you can run this to switch to our class group account:
```bash
newgrp csci5481
```

You can check if you're in other groups with this:
```bash
groups
```

### Launch and connect to an interactive computing node
- When you first log in to MSI, you will be on a "login" node. You are not allowed to run computations on this node. Instead, you can launch an interactive node for running computations with this command:

 ```bash
# Note: --ntasks-per-node is the number of cores you want
# and --mem-per-cpu is the RAM _per_ core, multiple these to get total memory
# -t is the time you want allowed
# Only request what you need
srun -N 1 --ntasks-per-node=4 --mem-per-cpu=4gb -t 02:00:00 -p agsmall --pty bash
 ```

This may take a while to finish running. It will log you directly in to the interactive node. Often you can see that this has happened because the start of the line in the terminal will say something like "yourusername@cn0077" or "yourusename@acn001" and it will be different from what it was on the previous line. If in doubt, you can run `hostname` to print out the name of the node. Login nodes usually start with `ahl` or `login` or `ln`. 

Note: if this fails to connect, please try logging back in and running this instead (requesting the `interactive` partition instead of the `agsmall` partition):
 ```bash
srun -N 1 --ntasks-per-node=4 --mem-per-cpu=4gb -t 02:00:00 -p interactive --pty bash
 ```

### Troubleshooting
  * If you have trouble connecting, try filling out the MSI user agreement here: https://www.msi.umn.edu/user-agreement.
  * Make sure you are on campus, connected to the the UofM network or eduroam network. Otherwise, MSI will block your computer from connecting. To get around this, you can also use a [University of Minnesota VPN](https://it.umn.edu/services-technologies/virtual-private-network-vpn). 
