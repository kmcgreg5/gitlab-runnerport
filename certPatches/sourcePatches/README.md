# Source Certification Patch Content and Explanations
* rmFilesFix.bash.go.patch
  * Applies to generated build directory cleanup commands.
  * Using `+` as a `find -exec` terminator is unsupported on z/OS. The terminator was changed to `;` instead.
  * As the `+` terminator runs a single command at the end of the search, when using the `;` terminator the `-depth` argument must be included when removing directories. This is to prevent `find` from removing a directory and subsequently trying to search it, causing a non-zero return.
* sectionTimeFix.bash.go.patch
  * Applies to the `section_start` and `section_end` informational messages.
  * The `date` `%s` format argument, which shows seconds since the epoch time, is unsupported on z/OS. It has been replaced with `${EPOCHSECONDS}`.