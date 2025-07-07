# Testcase Certification Patch Content and Explanations
All patch files are named in the format `<filename>.patch` or `<descriptor>-<filename>.patch` if there are multiple patches for one file.


## Features Unsupported on z/OS
Related testcases have been disabled using the `!zos` build flag.
* Kubernetes
  * exec_test.go.patch
  * feature_test.go.patch
  * helpers_kubernetes_test.go.patch
  * host_aliases_test.go.patch
  * kubernetes_integration_test.go.patch
  * kubernetes_test.go.patch
  * log_processor_test.go.patch
  * overwrites_test.go.patch
  * service_proxy_test.go.patch


* Docker
  * auth_test.go.patch
  * autoscaler_integration_test.go.patch
  * docker_command_integration_test.go.patch
  * docker_steps_integration_test.go.patch
  * linux_set_integration_test.go.patch
  * manager_integration_test.go.patch
  * terminal_integration_test.go.patch
  * volumes-manager_integration_test.go.patch


* Miscellanious
  * fleeting_integration_test.go.patch
    * This test case depends on an AWS image, which I do not believe would function on z/OS.


## Enabled Testcases
These are testcases that contain build flags. The `zos` build flag has been added so that they execute on z/OS.
* commander_unix_test.go.patch
* group_unix_test.go.patch
* killer_unix_integration_test.go.patch
* killer_unix_test.go.patch


## Unit Testcase Patches
* buildLimit-multi_test.go.patch
  * For a test case that checks that the runner will stop accepting jobs when a build limit is met.
  * The time of each job was increased to help it pass more reliably on z/OS.
* configReloading-multi_test.go.patch
  * For a test case that checks that the runner configuration is reloaded when it is modified on the system.
  * A sleep was added in between the creation of the configuration file and it's modification. To ensure enough time passes for it to be detected as changed.
* custom_test.go.patch
  * For a test case that checks for a 'file not found' error message when a cleanup attempts to delete a non-existant file.
  * The error message on z/OS is `No such file or directory` while `no such file or directory` was expected previously.


## Integration Testcase Patches
* integration_test.go.patch
  * A simple change to call the correct testing method in the testcase.
* shell_integration_test.go.patch
  * A collection of testcases that includes calls to `git-lfs`. `git-lfs` is not provided by IBM Open Enterprise Foundation, but it is available through the open source zopen package manager.
  * This change injects the `PATH` variable into the runner configuration. The `PATH` variable contains the zopen package managers `bin` directory so that `git-lfs` is made available and these testcases can execute successfully.
  * There might be a better way to do this, it is currently depending on the shell environment that launched the test cases.
