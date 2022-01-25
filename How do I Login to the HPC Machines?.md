# How do I Login to the HPC Machines?

## VPN Connection
Firstly, if you are off campus you should connect to the VPN. If you want to find the instructions about how to access and how to connect [check this site] (https://confluence.ku.edu.tr/kuhelp/ithelp/it-services/network-and-wireless/vpn-access).

## Windows
Use a secure shell client, e.g. [MobaXterm] (https://mobaxterm.mobatek.net/features.html)
1) Here is the direct link to ([Please download installer edition] (https://mobaxterm.mobatek.net/download-home-edition.html))
2) Once you have mobaxterm installed [follow this guide] (https://mobaxterm.mobatek.net/documentation.html)

Note if you have cygwin installed, you can open a cygwin-terminal and then use ssh the same as for Linux and Mac below.
If you aren’t sure what cygwin is, you can safely ignore the above line.

## Linux and Mac
Use ssh on the command line:

`ssh ku-username@login.kuacc.ku.edu.tr`

Note: KU username and password are your HPC username and password.

For visualization, you can use -X or -Y options:
### Linux:
`ssh username@login.kuacc.ku.edu.tr -Xl username`

### Mac:
`ssh username@login.kuacc.ku.edu.tr -Yl username`

-Visualization with X/Y options can slow down your computer. If you want visualization which is fast or you will submit an interactive job or running some Matlab code you may want to use VNC. To download VNC follow the steps on this page. For more information about the visualization visit [interactive jobs] (KUACC Guide/How do I Run My Job?/How do I interact with Jobs in Real Time?.md) page.
 
:sos: Remember that you are on the login nodes when you log into the cluster. Please do not use login nodes to run your jobs. It is important that the nodes are not used for computation so that other users can connect to the cluster. To run a job [visit this page] (KUACC Guide/How do I Run My Job?/How do I Write and Submit a Jobscript?.md).
