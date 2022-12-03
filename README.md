#### Extra Packages for Enterprise Linux, or simply EPEL, is one of the widely used repositories that provides standard additional packages for Enterprise Linux. All EPEL packages are maintained by the Fedora repo.

#### Let’s check the available repositories installed on our system :

```
[root@ip-172-31-84-51 ~]# dnf repolist
Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

repo id                      repo name
rhel-9-appstream-rhui-rpms   Red Hat Enterprise Linux 9 for x86_64 - AppStream from RHUI (RPMs)
rhel-9-baseos-rhui-rpms      Red Hat Enterprise Linux 9 for x86_64 - BaseOS from RHUI (RPMs)
rhui-client-config-server-9  Red Hat Enterprise Linux 9 Client Configuration
```

#### Checking if an updated version of package is available for the packages existing in our system.
```

[root@ip-172-31-84-51 ~]# dnf check-update

Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

Red Hat Enterprise Linux 9 for x86_64 - AppStream from RHUI (RP  17 MB/s |  15 MB     00:00    
Red Hat Enterprise Linux 9 for x86_64 - BaseOS from RHUI (RPMs)  12 MB/s | 6.9 MB     00:00    
Red Hat Enterprise Linux 9 Client Configuration                  16 kB/s | 2.0 kB     00:00    

kpartx.x86_64                                  0.8.7-12.el9_1.1       rhel-9-baseos-rhui-rpms   
krb5-libs.x86_64                               1.19.1-24.el9_1        rhel-9-baseos-rhui-rpms   
python-unversioned-command.noarch              3.9.14-1.el9_1.1       rhel-9-appstream-rhui-rpms
python3.x86_64                                 3.9.14-1.el9_1.1       rhel-9-baseos-rhui-rpms   
python3-libs.x86_64                            3.9.14-1.el9_1.1       rhel-9-baseos-rhui-rpms   
redhat-cloud-client-configuration.noarch       1-10.el9_0             rhel-9-appstream-rhui-rpms
tzdata.noarch                                  2022f-1.el9_1          rhel-9-baseos-rhui-rpms 
```


#### We first update the available package on our system for installing the EPEL repository:
 
 ```
 
 [root@ip-172-31-84-51 ~]# dnf -y update
 
 ```
 
 #### Finally, we can run install the EPEL repository :
 
 ```
[root@ip-172-31-84-51 ~]# dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

Last metadata expiration check: 0:01:59 ago on Sat 03 Dec 2022 05:00:28 AM UTC.
epel-release-latest-8.noarch.rpm                                145 kB/s |  24 kB     00:00    
Dependencies resolved.
================================================================================================
 Package                 Architecture      Version                Repository               Size
================================================================================================
Installing:
 epel-release            noarch            8-18.el8               @commandline             24 k

Transaction Summary
================================================================================================
Install  1 Package

Total size: 24 k
Installed size: 35 k
Is this ok [y/N]: y
Downloading Packages:
Running transaction check
Transaction check succeeded.
Running transaction test
Transaction test succeeded.
Running transaction
  Preparing        :                                                                        1/1 
  Installing       : epel-release-8-18.el8.noarch                                           1/1 
  Running scriptlet: epel-release-8-18.el8.noarch                                           1/1 
Many EPEL packages require the CodeReady Builder (CRB) repository.
It is recommended that you run /usr/bin/crb enable to enable the CRB repository.

  Verifying        : epel-release-8-18.el8.noarch                                           1/1 
Installed products updated.

Installed:
  epel-release-8-18.el8.noarch  
 ``` 

#### Checking Repolist :
```
 [root@ip-172-31-84-51 ~]# dnf repolist
Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

repo id                      repo name
epel                         Extra Packages for Enterprise Linux 8 - x86_64
rhel-9-appstream-rhui-rpms   Red Hat Enterprise Linux 9 for x86_64 - AppStream from RHUI (RPMs)
rhel-9-baseos-rhui-rpms      Red Hat Enterprise Linux 9 for x86_64 - BaseOS from RHUI (RPMs)
rhui-client-config-server-9  Red Hat Enterprise Linux 9 Client Configuration
```


#### To list the software packages that constitute the EPEL repository, run the command.

```
[root@ip-172-31-84-51 ~]# dnf --disablerepo="*" --enablerepo="epel" list available
Updating Subscription Management repositories.
Unable to read consumer identity

This system is not registered with an entitlement server. You can use subscription-manager to register.

Last metadata expiration check: 0:00:11 ago on Sat 03 Dec 2022 05:07:55 AM UTC.
Available Packages
3proxy.x86_64                                        0.8.13-1.el8                           epel
6tunnel.x86_64                                       0.13-1.el8                             epel
AMF-devel.noarch                                     1.4.26-1.el8                           epel
AMF-samples.noarch                                   1.4.26-1.el8                           epel
Agda.x86_64                                          2.5.3-14.el8                           epel
AusweisApp2.x86_64                                   1.22.3-1.el8                           epel
AusweisApp2-data.noarch                              1.22.3-1.el8                           epel
AusweisApp2-doc.noarch                               1.22.3-1.el8                           epel
BackupPC.x86_64                                      4.4.0-1.el8                            epel
BackupPC-XS.x86_64                                   0.62-1.el8                             epel
BibTool.x86_64                                       2.68-1.el8                             epel
CCfits.x86_64                                        2.5-14.el8                             epel
CCfits-devel.x86_64                                  2.5-14.el8                             epel
CCfits-doc.noarch                                    2.5-14.el8                             epel
CFR.noarch                                           0.151-4.el8                            epel
CFR-javadoc.noarch                                   0.151-4.el8                            epel
CGSI-gSOAP.x86_64                                    1.3.11-7.el8                           epel
CGSI-gSOAP-devel.x86_64                              1.3.11-7.el8                           epel

```

#### Installing a package from EPEL repository :

```

[root@ip-172-31-84-51 ~]# dnf --enablerepo="epel" install hping3


```
