# Importing from VMWare OVA
Using the aws cli on Windows, with a private key already set in my aws config for my root user.
OVA is uploaded to S3 already, in the rnebular-private bucket, in a folder called imports.


"aws ec2 import-image --cli-input-json <json-here>"

JSON for above command:
<json here after it's validated>


## Complete command:
aws ec2 import-image --cli-input-json "{  \"Description\": \"7-29-2018-RemotePC\", \"DiskContainers\": [ { \"Description\": \"cli import task\", \"UserBucket\": { \"S3Bucket\": \"rnebular-private\", \"S3Key\" : \"imports\RemotePC.ova" } } ]}"


## Foot-Notes:
For anyone doing this, I recommend using an IAM user or assumed role with permissions, instead of the root user.
For anyone lazy like me, root works fine. I rotate my keys often enough ;)

### References
A Blog post about it:
http://techgenix.com/importing-virtual-machine-amazon-ec2-part7/

AWS Guide for the import-image cli command:
https://docs.aws.amazon.com/cli/latest/reference/ec2/import-image.html

Amazon very high level import process doc (they like ambiguity):
https://aws.amazon.com/ec2/vm-import/
