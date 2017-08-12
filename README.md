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

