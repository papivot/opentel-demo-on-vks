# Prepare cluster

```
vcf plugin source update default --uri projects.packages.broadcom.com/vcf-cli/plugins/plugin-inventory:latest

vcf plugin search
vcf plugin sync
vcf plugin install cluster --version v3.4.1
vcf plugin install package --version v3.4.1

vcf package repository add standard-package-repo --url projects.packages.broadcom.com/vsphere/supervisor/packages/2025.8.19/vks-standard-packages:v2025.8.19 -n tkg-system
vcf package available list -n tkg-system --wide

vcf package available get cert-manager.kubernetes.vmware.com -n tkg-system
vcf package available get contour.kubernetes.vmware.com -n tkg-system
vcf package available get cluster-autoscaler.kubernetes.vmware.com/1.33.0+vmware.1-vks.1 -n tkg-system --default-values-file-output values.yaml

# Modify the values.yaml for the autoscaler

vcf package install cert-manager-pkg -n tkg-system --package cert-manager.kubernetes.vmware.com --version 1.18.2+vmware.1-vks.
vcf package install cluster-autoscaler-pkg -n tkg-system --package cluster-autoscaler.kubernetes.vmware.com --version 1.33.0+vmware.1-vks.1 --values-file ./autoscaler-data-values.yaml
vcf package install contour-pkg -n tkg-system --package contour.kubernetes.vmware.com --version 1.32.0+vmware.1-vks.1 --values-file ./contour-data-values.yaml

```