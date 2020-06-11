## Zowe commands to setup profile
zowe profiles create zosmf LC --host 192.86.32.250 --port 10443 --ru false --user Z81587 --pass ZCOBOL --ow

zowe zosmf check status

## Download files to local folders
zowe files list ds "Z81587.*"

zowe files list am "Z81587.CBL"

zowe files download am "Z81587.CBL" -e ". cbl"
zowe files download am "Z81587.JCL" -e ". jcl"


## Work on Hello World

### Submit the job
zowe jobs submit ds "Z81587.JCL(HELLO)" --vasc


### Submit job and wait for OUTPUT status

zowe jobs submit ds "Z81587.JCL(HELLO)" --wfo

#### List the files
zowe jobs list sfbj JOB04004

#### Download a specific file
zowe jobs view sfbi JOB04004 105

### Submit the job and download the files

zowe jobs submit ds "Z81587.JCL(HELLO)" -d ./z81587/output

