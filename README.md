# ArgoCD Resources

This repo is being monitored by ArgoCD for any new resources to create.

## Some potential useful commands

I used these commands to copy over helm charts in the demo and committed them to the repo.

```
cp -r /Users/nprice/Code/TW/backstage-crossplane/crossplane-argocd-examples/crossplane/managed-resources/aws-s3-chart/* /Users/nprice/Code/TW/backstage-crossplane/argocd-resources/argocd/resources/s3buckets/
cp -r /Users/nprice/Code/TW/backstage-crossplane/crossplane-argocd-examples/crossplane/managed-resources/aws-vpc-chart/* /Users/nprice/Code/TW/backstage-crossplane/argocd-resources/argocd/resources/vpcs/
cp -r /Users/nprice/Code/TW/backstage-crossplane/crossplane-argocd-examples/crossplane/managed-resources/aws-ec2-chart/* /Users/nprice/Code/TW/backstage-crossplane/argocd-resources/argocd/resources/ec2s/
cp -r /Users/nprice/Code/TW/backstage-crossplane/crossplane-argocd-examples/crossplane/managed-resources/aws-lambda-chart/* /Users/nprice/Code/TW/backstage-crossplane/argocd-resources/argocd/resources/lambda/
cp -r /Users/nprice/Code/TW/backstage-crossplane/crossplane-argocd-examples/helm-apps/example-voting-app/* /Users/nprice/Code/TW/backstage-crossplane/argocd-resources/argocd/resources/apps/

cd /Users/nprice/Code/TW/backstage-crossplane/argocd-resources
git add .
git commit -am "adding new resources"
git push
```

The following commands are to remove them (the revser of the above).

```
find '/Users/nprice/Code/TW/backstage-crossplane/argocd-resources/argocd/resources/s3buckets/' -maxdepth 3 -not -name 'README.md' -delete
find '/Users/nprice/Code/TW/backstage-crossplane/argocd-resources/argocd/resources/backstage-s3buckets/' -maxdepth 3 -not -name 'README.md' -delete
find '/Users/nprice/Code/TW/backstage-crossplane/argocd-resources/argocd/resources/vpcs/' -maxdepth 3 -not -name 'README.md' -delete
find '/Users/nprice/Code/TW/backstage-crossplane/argocd-resources/argocd/resources/ec2s/' -maxdepth 3 -not -name 'README.md' -delete
find '/Users/nprice/Code/TW/backstage-crossplane/argocd-resources/argocd/resources/lambda/' -maxdepth 3 -not -name 'README.md' -delete
find '/Users/nprice/Code/TW/backstage-crossplane/argocd-resources/argocd/resources/apps/' -maxdepth 3 -not -name 'README.md' -delete
cd /Users/nprice/Code/TW/backstage-crossplane/argocd-resources
git add .
git commit -am "removing resources"
git push
```

## Potential clean up

The following commands have been used when the platform hasn't self cleaned up the resources.

```
kubectl patch function neil-lambda  -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch instance neil-ec2-instance-dev-ap-southeast-2  -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch securitygrouprule neil-ec2-instance-dev-sg-ingress1-ap-southeast-2  -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch securitygroup neil-ec2-instance-dev-sg-ap-southeast-2  -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch routetableassociation neil-vpc-dev-private-routetableassociation-ap-southeast-2a  -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch routetableassociation neil-vpc-dev-private-routetableassociation-ap-southeast-2b  -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch routetableassociation neil-vpc-dev-public-routetableassociation-ap-southeast-2a  -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch routetableassociation neil-vpc-dev-public-routetableassociation-ap-southeast-2b  -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch route neil-vpc-dev-private-route-ap-southeast-2   -p '{"metadata":{"finalizers":[]}}' --type=merge 
kubectl patch route neil-vpc-dev-public-route-ap-southeast-2   -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch routetable neil-vpc-dev-public-routetable-ap-southeast-2   -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch routetable neil-vpc-dev-private-routetable-ap-southeast-2   -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch natgateway neil-vpc-dev-nat-ap-southeast-2  -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch internetgateway neil-vpc-dev-igw-ap-southeast-2  -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch subnet neil-vpc-dev-private-subnet-ap-southeast-2a -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch subnet neil-vpc-dev-private-subnet-ap-southeast-2b -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch subnet neil-vpc-dev-public-subnet-ap-southeast-2a -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch subnet neil-vpc-dev-public-subnet-ap-southeast-2b -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch eip neil-vpc-dev-eip-ap-southeast-2  -p '{"metadata":{"finalizers":[]}}' --type=merge
kubectl patch vpc neil-vpc-dev-ap-southeast-2 -p '{"metadata":{"finalizers":[]}}' --type=merge

