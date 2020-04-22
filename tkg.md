# Deploying VMware's Tanzu Kubernetes Grid (TKG) clusters using Container Service Extension

Container Service Extension 2.6.0 enables orchestration of VMware's TKG Kubernetes clusters in VMware vCloud Director powered clouds. It comes with the built-in capability to leverage VMware TKG through the TKG template. In order to turn on this capability, please see the section **Creating VMware TKG Template using Container Service Extension**. The details of VMware TKG template used in Container Service Extension are highlighted in the section **VMware TKG Template Details**.

---

## Container Service Extension (CSE) Reference Links

- [Container Service Extension official docs](https://vmware.github.io/container-service-extension/INTRO.html)
- [Container Service Extension on pypi](https://pypi.org/project/container-service-extension/)
- [Container Service Extension Github](https://github.com/vmware/container-service-extension)

---

## VMware TKG Template Details

| Attribute                   | Value                                                                                                            |
|-----------------------------|------------------------------------------------------------------------------------------------------------------|
| Template name               | ubuntu-16.04_tkg-1.17_weave-2.5.2                                                                             |
| Latest Revision             | 1                                                                                                                |
| Catalog item name           | ubuntu-16.04_tkg-1.17_weave-2.5.2_rev1                                                                        |
| Template details URL        | <https://raw.githubusercontent.com/andrew-ni/container-service-extension-templates/tkg/template.yaml>     |
| Ubuntu version              | [16.04](https://cloud-images.ubuntu.com/releases/xenial/release-20180418/ubuntu-16.04-server-cloudimg-amd64.ova) |
| Docker version              | 18.09.7 (docker-ce=5:18.09.7\~3-0\~ubuntu-xenial)                                                                |
| Kubernetes version          | [VMware TKG 1.17.3](https://hub.vmware.com/releases/tanzu-1-17-releases/#1173vmware1)                   |
| Weave version               | [2.5.2](https://www.weave.works/docs/net/latest/overview/)                                                       |
| Default compute policy name | tkg                                                                                                   |
| Default number of vCPUs     | 2                                                                                                                |
| Default memory              | 2048 mb                                                                                                          |

---

## Creating VMware TKG Template using Container Service Extension

*A CSE config file should be created and should contain your VMware vCloud Director details. More CSE config file details can be found [here](https://vmware.github.io/container-service-extension/CSE_ADMIN.html#configfile)*

1. In the CSE config file, change the value of the key `remote_template_cookbook_url` to  `https://raw.githubusercontent.com/andrew-ni/container-service-extension-templates/tkg/template.yaml`. This change enables CSE to view the source of VMware TKG Template.
2. Create VMware TKG template in VMware vCloud Director using CSE's command-line interface by choosing one of these two ways:
   - Install or re-install CSE 2.6.0 on VMware vCloud Director to create new VMware TKG template as specified in the CSE config file. The existing templates that were installed by CSE will not be affected.
     - ```$ cse install -c path/to/myconfig.yaml```
   - Use CSE's template install command to create new VMware TKG template after CSE is already installed on VMware vCloud Director (check VMware TKG Template Details section for parameter values).
     - ```$ cse template install -c path/to/myconfig.yaml TEMPLATE_NAME TEMPLATE_REVISION_NUMBER```
3. In the VMware vCloud Director organization specified in the CSE config file, you should see the VMware TKG template in the catalog (also specified in the CSE config file).

Users can now create VMware Essential PKS Kubernetes clusters using CSE. For VMware vCloud Director 10, please follow the section **Deployment of Kubernetes clusters from VMware TKG Template**

---
