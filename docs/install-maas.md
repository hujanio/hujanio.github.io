### About MAAS

**Hujan** using MAAS to deploy Operating System to your environment. MAAS (Metal as a Service) is an open-source tool that lets you build a data centre from bare-metal servers.  

You can discover, commission, deploy, and dynamically reconfigure a large network of individual units. MAAS converts your hardware investment into a cohesive, flexible, distributed data centre, with a minimum of time and effort.

### Requirements

The entire environment will consist of a single MAAS system. This MAAS cluster will contain a single zone, with the MAAS system (region and rack controllers).  

Here are the hardware requirements :  
- CPU : 4 Core.  
- Memmory : 8 GiB.  
- Disk : 50 GiB.  
- 1 NIC.  

See [MAAS requirements](https://maas.io/docs/snap/2.9/ui/maas-requirements) in the MAAS documentation for more detailed information on what a MAAS system may require.  

### Setup MAAS

Here is a concise summary of how to install and initialise MAAS.  

1. Install MAAS and Testdb for MAAS
```
sudo snap install maas --channel=2.9/stable
sudo snap install maas-test-db
```

2. First MAAS initialisation
```
sudo maas init region+rack --maas-url http://[maas-url]:5240/MAAS --database-uri maas-test-db:///
```

3. Create MAAS admin user
```
sudo maas createadmin --username admin --password s3cr3tp455w0rd --email admin@admin.id --ssh-import gh:[username]
```

4. Get API Key
```
sudo maas apikey --username admin > ~/admin-api-key
```

For production configuration you need to setup PostgreSQL.

