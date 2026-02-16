# Project for provisioning an simple infrastructure with Terraform and Ansible

The goal of this repo is to produce a demo infrastructure for an immaginary environment requiring provisioning infrasture and configuring a full environment following these contraints:

- use a Hyper-V virtualized environment
- use Terraform for provisioning the infrastruture
- use Ansible for configuring the environment.

## Virtual machines to provision

1. Windows Server 2025 named `dc` with following configurations:
    - The AD and DNS roles installed
    - configure the domain `demo.local`
    - provision 2 user account (tbd), 2 computer accounts (`sql` and `web`) and 2 groups (tbd)
    - computer accounts should be just provisioned and disabled, but don't disable if these already exist and already enabled
    - other requirements that might arise, as needed

2. Windows Server 2025 named `sql` with following configurations:
     - add the server to the `demo.local` domain
     - install SQL server 2022 (2025)
     - create a sql account `cmsuser` and a database named `cms`. provide sql account access `db_ddladmin`, `db_datareader` and `db_datawriter` sql rolesn to the new database

3. Windows Server 2025 named `web` with following configurations:
     - add the server to the `demo.local` domain
     - install iis role
     - install dotnet 10 web hosting version
     - download and install the orchard cms on the vm
     - configure the cms with the default instance to use the `sql` server for data persistence

## Non-functional requirements

1. Environment should be using a vm template
2. Running the script should not break an already deployed environment
3. Other to add as the env will evolve