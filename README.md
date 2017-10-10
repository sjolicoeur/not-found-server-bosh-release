```
➜  /Users/pivotal/workspace mkdir not-found-server                                                                                                                          
➜  /Users/pivotal/workspace  cd not-found-server                                                                                                                            system
➜  /Users/pivotal/workspace/not-found-server bosh init-release                                                                                                              system
Succeeded

➜  /Users/pivotal/workspace/not-found-server/src git clone git@github.com:sjolicoeur/pivotal-io-404.git                                                                     system
Cloning into 'pivotal-io-404'...
Warning: Permanently added the RSA host key for IP address '192.30.255.113' to the list of known hosts.
remote: Counting objects: 26, done.
remote: Compressing objects: 100% (9/9), done.
remote: Total 26 (delta 4), reused 10 (delta 3), pack-reused 14
Receiving objects: 100% (26/26), 7.96 KiB | 7.96 MiB/s, done.
Resolving deltas: 100% (5/5), done.
➜  /Users/pivotal/workspace/not-found-server/src


➜  /Users/pivotal/workspace/not-found-server bosh generate-job pivotal-io-404                                                                                               system
Succeeded

➜  /Users/pivotal/workspace/not-found-server bosh generate-package nginx                                                                                                    system
Succeeded


download the files first
➜  /Users/pivotal/workspace/not-found-server bosh add-blob ~/Downloads/nginx-1.12.1.tar.gz  nginx/nginx-1.12.1.tar.gz                                                       system
Added blob 'nginx/nginx-1.12.1.tar.gz'

download the files first

➜  /Users/pivotal/workspace/not-found-server bosh add-blob ~/Downloads/pcre-8.40.tar.gz nginx/pcre-8.40.tar.gz                                                              system
Added blob 'nginx/pcre-8.40.tar.gz'

Succeeded


➜  /Users/pivotal/workspace/not-found-server bosh upload-release                                                                                                            system
Using environment 'https://35.190.180.192:25555' as client 'admin'

########################################################### 100.00% 2.06 KB/s 0s
Task 650

Task 650 | 00:10:28 | Extracting release: Extracting release (00:00:00)
Task 650 | 00:10:28 | Verifying manifest: Verifying manifest (00:00:00)
Task 650 | 00:10:28 | Resolving package dependencies: Resolving package dependencies (00:00:00)
Task 650 | 00:10:28 | Processing 2 existing packages: Processing 2 existing packages (00:00:00)
Task 650 | 00:10:28 | Processing 1 existing job: Processing 1 existing job (00:00:00)
Task 650 | 00:10:28 | Release has been created: not-found-server/0+dev.2 (00:00:00)

Task 650 Started  Sat Aug 12 00:10:28 UTC 2017
Task 650 Finished Sat Aug 12 00:10:28 UTC 2017
Task 650 Duration 00:00:00
Task 650 done

Succeeded
➜  /Users/pivotal/workspace/not-found-server



➜  /Users/pivotal/workspace/onboarding-week-pair-2/cf-deployment git:(master) ✗ bosh -d cf deploy --vars-store cf-deployment-vars.yml -o operations/gcp.yml -o operations/scale-to-one-az.yml cf-deployment.yml -o operations/enable-privileged-container-support.yml
Using environment 'https://35.190.180.192:25555' as client 'admin'

➜  /Users/pivotal/workspace/onboarding-week-pair-2 bbl ssh-key                                                                                       system
➜  /Users/pivotal/workspace/onboarding-week-pair-2 bbl ssh-key > key.pem                                                                             system
➜  /Users/pivotal/workspace/onboarding-week-pair-2 chmod 600 key.pem                                                                                 system
➜  /Users/pivotal/workspace/onboarding-week-pair-2 bosh ssh not-found-server/cc2853f0-9325-46cb-9946-4d1ace70b405 -d cf --gw-user=jumpbox --gw-private-key=key.pem

➜  /Users/pivotal/workspace/not-found-server git:(master) ✗ bosh vms                                                                                                        system
Using environment 'https://35.190.180.192:25555' as client 'admin'


➜  /Users/pivotal/workspace/onboarding-week-pair-2/cf-deployment git:(master) ✗ bosh -d cf deploy --vars-store cf-deployment-vars.yml -o operations/gcp.yml -o operations/scale-to-one-az.yml cf-deployment.yml -o operations/enable-privileged-container-support.yml
Using environment 'https://35.190.180.192:25555' as client 'admin'

[...]


Task 759

Task 759 | 01:34:18 | Preparing deployment: Preparing deployment (00:00:02)
Task 759 | 01:34:24 | Preparing package compilation: Finding packages to compile (00:00:00)
Task 759 | 01:34:24 | Updating instance not-found-server: not-found-server/cc2853f0-9325-46cb-9946-4d1ace70b405 (0) (canary) (00:01:13)

Task 759 Started  Sat Aug 12 01:34:18 UTC 2017
Task 759 Finished Sat Aug 12 01:35:37 UTC 2017
Task 759 Duration 00:01:19
Task 759 done

Succeeded
➜  /Users/pivotal/workspace/onboarding-week-pair-2/cf-deployment git:(master) ✗


not-found-server/cc2853f0-9325-46cb-9946-4d1ace70b405:~# monit summary
The Monit daemon 5.2.5 uptime: 0m

Process 'pivotal-io-404'            running
System 'system_localhost'           running
not-found-server/cc2853f0-9325-46cb-9946-4d1ace70b405:~# monit status
The Monit daemon 5.2.5 uptime: 1m

Process 'pivotal-io-404'
  status                            running
  monitoring status                 monitored
  pid                               25364
  parent pid                        1
  uptime                            2m
  children                          1
  memory kilobytes                  772
  memory kilobytes total            3620
  memory percent                    0.0%
  memory percent total              0.0%
  cpu percent                       0.0%
  cpu percent total                 0.0%
  data collected                    Sat Aug 12 01:36:37 2017

System 'system_localhost'
  status                            running
  monitoring status                 monitored
  load average                      [0.01] [0.01] [0.00]
  cpu                               0.0%us 0.0%sy 0.1%wa
  memory usage                      100720 kB [2.6%]
  swap usage                        0 kB [0.0%]
  data collected                    Sat Aug 12 01:36:37 2017

not-found-server/cc2853f0-9325-46cb-9946-4d1ace70b405:~#

```
---- more notes


${BOSH_INSTALL_TARGET}/ == /var/vcap/jobs/<job name>
${BOSH_INSTALL_TARGET}/<dependency name>

https://github.com/sjolicoeur/not-found-server-bosh-release/blob/master/packages/nginx/packaging -> will install a compiled nginx inside of  ${BOSH_INSTALL_TARGET}/nginx to do so it will unzip 

- nginx/nginx-1.12.1.tar.gz
- nginx/pcre-8.40.tar.gz

inside /var/vcap/jobs/nginx


https://github.com/sjolicoeur/not-found-server-bosh-release/blob/master/packages/pivotal-io-404/packaging -> will add a folder public with 
${BOSH_INSTALL_TARGET}/public/error.html in it


https://github.com/sjolicoeur/not-found-server-bosh-release/blob/master/jobs/pivotal-io-404/spec -> specifies what is needed in packages and an env var APP_ROOT. the templates are for boot up scripts and where they should be created bin, etc. https://github.com/sjolicoeur/not-found-server-bosh-release/tree/master/jobs/pivotal-io-404/templates
