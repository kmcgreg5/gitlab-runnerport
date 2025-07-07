# Source Patch Content and Explanations
These are source patches made by the IBM GO team when initially porting the gitlab runner to z/OS. All patch files are named in the format `<filename>.patch`.


### `zos` Build Flag Additions
* commander_unix.go.patch
* config_unix.go.patch
* dump_unix.go.patch
* job_unix.go.patch
* killer_unix.go.patch
* wrapper_unix.go.patch
* zip_extra_unix.go.patch


### `!zos` Build Flag Additions
* service_portable.go.patch

### Source Patches
* ops_unix.go.patch
  * Adds handling for `zos` to the `lchtimes` method.
* service_zos.go.patch
  * A new source file containing the `zos` services' configuration.
