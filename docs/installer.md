The installer menu is used to start deployment. On this menu you can select which machine will use for controller node, compute node and more.

To start deployment go to Installer menu.

![installer page](assets/images/deploy1.png "installer page")

From this page, you can select which machine to deploy. From this entry `Hujan` will automaticaly create inventory list.

![add server](assets/images/deploy3.png "add server")

After that select save server and next to inventory page. On this page you can select the server role, which will be added to `kolla-ansible` inventory.

![inv page](assets/images/deploy4.png "Inventory Page")

Click on `Add Inventory`.

![add inv](assets/images/deploy5.png "add inventory")

Click `Save Inventory` and next to `Globals Configuration` menu.

![global page](assets/images/deploy7.png "Global Config Page")

On `Global Configuration` menu you can customize your openstack configuration base on [globals.yml](https://github.com/openstack/kolla-ansible/blob/master/etc/kolla/globals.yml) from `kolla-ansible`. Then click `deploy`.

![finish deploy](assets/images/finish-deploy.png "finish deployment")


![openstack login page](assets/images/openstack-login.png "openstack login")