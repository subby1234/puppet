# puppet
On Master
sudo apt update
sudo apt install wget
wget https://apt.puppetlabs.com/puppet-release-bionic.deb
sudo dpkg -i puppet-release-bionic.deb
sudo apt install puppet-master
apt policy puppet-master
sudo systemctl status puppet-master.service
sudo vim /etc/default/puppet-master
--JAVA-ARGS="Xms512m -Xmx512m"
sudo systemctl restart puppet-master.service

sudo ufw allow8140/tcp

//change code
sudo mkdir -p /etc/puppet/code/environments/production/manifests/
sudo nano /etc/puppet/code/environments/production/manifests/site.pp
file {'/tmp/it_works.txt":
  ensure	=> present,
  mode		=> '0644',
  content	=>"It works on ${}ipaddres_ethe}!\n",
  }
  
  
sudo systemctl restart puppet-master
.............................................................  
  
Puppet Agent
sudo apt update
sudo apt install wget
wget https://apt.puppetlabs.com/puppet-release-bionic.deb
sudo dpkg -i puppet-release-bionic.deb
sudo apt install puppet

sudo systemstl start puppet
sudo systemstl enable puppet
.........................................

master
sudo puppet cert list

sudo puppet cert sign --all

.............................

master

//change code
sudo mkdir -p /etc/puppet/code/environments/production/manifests/
sudo nano /etc/puppet/code/environments/production/manifests/site.pp
file {'/tmp/it_works.txt":
  ensure	=> present,
  mode		=> '0644',
  content	=>"It works on ${}ipaddres_ethe}!\n",
  }
  .........................................................................
  
  Here is a breakdown of the commands and steps provided for setting up a Puppet master-slave architecture and applying manifests to create a file on the nodes:

**On Puppet Master:**
1. Update package lists and install `wget`:
   ```
   sudo apt update
   sudo apt install wget
   ```
2. Download and install the Puppet repository package:
   ```
   wget https://apt.puppetlabs.com/puppet-release-bionic.deb
   sudo dpkg -i puppet-release-bionic.deb
   ```
3. Install Puppet master:
   ```
   sudo apt install puppet-master

   ```
4. Check the policy for the puppetmaster package:
   ```
   apt policy puppet-master

   ```
5. Check the status of the Puppet master service:
   ```
   sudo systemctl status puppet-master.service
   ```
6. Edit the Puppet master configuration file:
   ```
   sudo vim /etc/default/puppet-master
   --JAVA-ARGS="Xms512m -Xmx512m"
   ```
7. Restart the Puppet master service:
   ```
   sudo systemctl restart puppet-master.service
   ```
8. Allow traffic on port 8140:
   ```
   sudo ufw allow 8140/tcp
   ```



9. Create a manifest to create a file:
   ```
   sudo mkdir -p /etc/puppet/code/environments/production/manifests/
   sudo nano /etc/puppet/code/environments/production/manifests/site.pp
   file { '/tmp/it_works.txt':
     ensure  => present,
     mode    => '0644',
     content => "It works on ${ipaddress_eth0}!\n",
   }
   ```
   
Make manifests

cd /etc/puppet/code/environments/production/manifests


sudo mkdir -p environments/production/manifests


10. Restart the Puppet master service:
    
    sudo systemctl restart puppet-master

**On Puppet Agent (Slave Node):**
1. Update package lists and install `wget`:
   ```
   sudo apt update
   sudo apt install wget
   ```
2. Download and install the Puppet repository package:
   ```
   wget https://apt.puppetlabs.com/puppet-release-bionic.deb
   sudo dpkg -i puppet-release-bionic.deb
   ```
3. Install Puppet:
   ```
   sudo apt install puppet
   
   
   sudo nano /etc/hosts
   masterip puppet
   
4. Start and enable the Puppet service:
   ```
   sudo systemctl start puppet
   sudo systemctl enable puppet
   ```

On Master.

sudo puppet cert list
sudo puppet cert sign ip-172-31-93-207.ec2.internal
  
sudo systemctl restart puppet-master
....................................

Slave has to request for the changes.....


cd /tmp
ls

sudo puppet agent --test

sudo puppet agent -t


ls
