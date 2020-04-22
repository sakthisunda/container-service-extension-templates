
Users can now create VMware Essential PKS Kubernetes clusters using CSE. For VMware vCloud Director 10, please follow the section **Deployment of Kubernetes clusters from VMware TKG Template**


## Deployment of Kubernetes clusters from VMware TKG Template

VMware TKG template created by CSE has a default compute policy "tkg". This policy is used to restrict Kubernetes cluster deployments to organization VDCs that have the matching policy in VMware vCloud Director. In order to enable Kubernetes cluster deployments using this template, system administrator needs to add the policy to the desired organization VDCs. More information on how CSE uses compute policies can be found [here](TODO)

Use CSE's command line interface to run below commands to add the policy to an organization VDC.

```bash
# must be logged in as system administrator
$ vcd login VCD_IP system administrator

# assign 'essential-pks' compute policy to your org VDC
$ vcd cse ovdc compute-policy add tkg -o ORG_NAME -v OVDC_NAME

# confirm that the compute policy is assigned to your org VDC
$ vcd cse ovdc compute-policy list -o ORG_NAME -v OVDC_NAME
```

*Only system administrator can use `vcd cse ovdc compute-policy ...` commands*

*Restricting deployments from VMware TKG template is only available on VMware vCloud Director 10. There is no way to restrict deployments from VMware TKG template on older VMware vCloud Director versions.*

Please refer to [here](TODO) for further information on enabling VMware TKG
