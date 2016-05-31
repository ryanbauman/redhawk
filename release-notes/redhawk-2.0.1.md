## REDHAWK Release Notes, Version 2.0.1
The effort in REDHAWK 2.0.1 focused on:

* Enhancing the level of control that a system deployer has to customize the reservation schema used to manage computing resources.
* Adding Python operators and Java methods to simplify common arithmetic operations on BulkIO time stamps.
* Addressing numerous Discrepancy Reports (DRs).

### IDE Improvements
* In Diagrams, duplicate connections between the same two Ports are displayed in yellow and show a warning.
* In the Sandbox, Components and Devices now display the Component or Device usage name rather than the Component’s or Device’s name.
* In the SAD Properties Editor, the name of the Properties are now displayed rather than the ID. If no name is available, the ID is displayed.
* An improved failure message is displayed for a Waveform installation failure.

###Core Framework Improvements
* Refactored auto-generated test script for Components to use the Sandbox.
* Added reservation floor to GPP so that when an Application is deployed, the amount reserved per Component is definable by the system user.
* Provided Timestamp Helper Methods that add/subtract two time stamp objects and print time stamp values.
* Added generation of getters and setters for Java struct property fields.

### IDE Fixes
* Fixed issue so refreshing the IDL library now updates the library.
* Fixed errors in generated spec files that prevented macro expansion.
* Fixed issue involving certain scenarios when the palette was loaded and an error occurred.
* Fixed issue so host collocation names can now be renamed.
* Updated Sandbox so that command-line Properties are not passed to Resource.initializeProperties().
* Fixed editors so when opened, items under the Target SDR are now read-only.
* Fixed update sites in IDE to use Mars not Luna.
* Updated IDE to include JacORB feature.
* Fixed Sandbox so that Properties of kind Property are not passed to Resource.configure() at launch.
* Fixed Sandbox so terminating a Waveform running in the Sandbox via the REDHAWK Explorer actually terminates the Waveform.
* Fixed issue so when opening the Component editor for a resource in the Sandbox, or the Explorer for a Waveform, an "Unsupported content" dialog and related error messages are not displayed in the console. Additionally, in the Editor view, three tabs no longer display blank content for each of the XML files.
* Fixed Chalkboard so releasing a Component no longer terminates the Component but actually releases the Component.
* Updated Devices so when a namespaced Device is dragged-and-dropped onto the Device Manager Chalkboard, it no longer is displayed in yellow and does not display an error.
* Fixed C++ workspace projects so when launched in the Sandbox, they now use entrypoint to execute.
* Fixed Sandbox so launching Waveforms that override a simplesequence no longer causes errors.
* Fixed Python Sandbox so when Components are launched, they have configure and property kind Properties passed to them in addition to execparams.
* Fixed Chalkboard so the context menu for Components of Domain Waveforms no longer displays Terminate as an available option.
* Fixed FEI Device Wizard so if a project name is name spaced, clicking Finish in the wizard no longer causes an error.
* Updated Node Diagrams so when connecting Ports between figures that have been collapsed, an error no longer occurs if the connection is ambiguous and the IDE prompts the user.
* Fixed SCD files in new projects to include the new CF.PropertyEmitter interface.
* Fixed DCD files so if they reference a non-existent SPD file for the Device Manager, the Overview tab in the DCD Editor functions.
* Fixed Redhawk Explorer view so if the ’name’ attribute is missing in a DCD, SPD, or SAD file in the SDRROOT, all items are still displayed under the Target SDR.
* Fixed DCD editor so if a Service is manually added in the XML tab, the Diagram tab reflects it.
* Updated code as a result of recent updates in Graphiti.
* Updated SAD/DCD diagrams to always fully reflect changes made to the underlying XML file.
* Fixed possible deadlock in UI thread.
* Updated Diagrams so renaming a Component no longer causes an error.
* Fixed issue when creating a FindBy, the FindBy was not allowed inside a host collocation; however, if the host collocation covered the FindBy in the Diagram, the FindBy sat on top of it making it appear like it was inside the host collocation.
* Fixed Diagram palette filter to search on the full Component name.
* Fixed the DCD Diagram palette to refresh with SDR root.
* Fixed issue so plot connection error does not display when making connections with Waveform external Ports.
* Fixed issue so a new Domain can be added with corbaloc or IOR syntax.
* Fixed SAD and DCD editor to allow Property value overrides for read-only command line Properties.
* Fixed event Property error when upgrading.
* Fixed project update so configure/execparam Properties are changed to a new Property.

### Core Framework Fixes
* Added a documentation note regarding performing a source upgrade from 1.8 to 2.0.
* Provided instructions on how to access Domain Manager and Application in comments for generated Components.
* Updated comments for generated Components to use stream-based input rather than getPacket.
* Updated bluefile_helpers to support numpy >= 1.9.0.
* Eliminated Makefile.am warnings on Ubuntu 14.04.
* Updated installation so when installing from source, if dependencies are not already present on the host or a valid PYPI is not accessible, the installation will fail.
* Enabled and verified support for xsd >= 3.3.0.
* Updated the generated configure.ac file for Octave Components by omitting a call to the RH_SOFTPKG_CXX macro. This update resolved configuration failures when dependencies did not have a valid pkgconfig, which is not present for noarch packages.
* Updated the redhawk.sh script in /etc/profile.d to fix LD_LIBRARY_PATH set issues.
* Added newline at end of EventChannelManager.idl.
* Updated CF tests so they can be run without BulkIO.
* Updated BurstIO testing so it no longer requires the libraries to be installed.
* Added regression test to verify that Waveform allocations are consolidated into a single allocation call when allocation Properties do not overlap.
* Renamed generated unit test testScaBasicBehavior to testRHBasicBehavior.
* Updated generated Ports in C++ and Java to report the most specific CORBA repid in getPortSet().
* Updated Python Components to only report Python MessageConsumer Ports as bi-directional, not MessageSupplier Ports.
* Updated Java BulkIO InFilePort to return the expected repid.
* Updated C++ GPP to manage Components as process groups and harmonize difference between Python and C++ GPP and changed timeouts to more sensible values.
* GPP Updated C++ GPP to set the process group ID during launch and then terminate based on the group ID if a Component does not die.
* Modified sb.launch() to allow overriding property kind Properties.
* Added support to properties.py for conversion of non base 10 strings.
* Updated py2prf so when exporting Properties to xml, simplesequence and structsequence are correct.
* Fixed Application launch so that Component command line Properties with no value do not get included in the incorrect initialization step.
* Fixed Sandbox DataSourcepush() to honor the EOS flag at the end of large pushes when the total size is an exact multiple of the packet size.
* Fixed Python Sandbox so it does not call initializeProperties() after the IDE calls initializeProperties().
* Fixed Python Sandbox so Java Components do not fail in Sandbox when the name Service is not running.
* Fixed DataSink so it honors the SRI subsize and returns a frame matrix.
* Improved feedback when an XML parsing error occurs.
* Modified Python PRF parser definition so app_prop is not part of the PRF parser definition for the struct.
* Fixed Python Service logging level so DEBUG_LEVEL is honored.
* Resolved issues when invalid Port names are used in Service connections.
* Fixed internal UUID module so generated UUID uses versions 1 or 4 and randomizes the MAC address.
* Fixed Device Manager to only report child processes as having exited when the child process terminates, ignoring non-fatal signals.
* Fixed Application stop to continue to stop all of the Components in an Application even if one fails, still throwing an exception at the end.
* Fixed Domain Manager memory leaks from parsers for Properties and fixed minor leaks with _ptr usage.
* Extended the Domain Manager to handle Application registrations locally.
* Added test for backwards compatibility with partial struct configuration.
* Fixed Python Sandbox to ensure that only simple Properties are passed on the command line, and that non-overridden command line Properties are not included in initializeProperties().
* Fixed issues with validating SAD file from installApplication() and createApplication() and issue with default command line option for new Properties.
* Fixed Connection Manager so connections to Applications cannot be deferred, and connections that cannot be deferred are deleted when the endpoint goes away.
Modified test Component cpp_with_deps to build on Ubuntu 14.04.
* Fixed issue to prevent deadlock when a Device Manager shuts down at the same time one of the Applications deployed to its Devices is released.
* Added semantic checking to the contents of a Waveform SAD.xml file and its associated Components and softpackage dependencies.
* Updated Python module to recognize external Ports that are in a host collocation block.
* Updated Domain Manager to handle IDM Channel messages.
* Added new interface extensions on core services to Python package.
* Added autotools-generated files to clean up for REDHAWK Library Projects.
* Fixed Python code generator to assign the default values for inherited Properties in the base class __init__() method instead of at the class definition level.
* Fixed launch failure for generated Java FEI Devices with additional tuner status fields.
* Added source to FEI JAR files.
* Modified the GPP to release all reservations for a Waveform.
* Added additional tests for compliant and non-compliant soft package dependencies.
* Modified Sandbox MessageSource to use messageId member.
* Fixed override of instance values for Components launched through the Python Sandbox interface running in the IDE.
* Fixed race condition in BulkIO unit tests for SDDS and Vita49.
* Added proper type checking for Properties in Python Components.
* Added handling for spurious CORBA errors on Component initialization while running QA tests that launch and release large numbers of Components.
* Fixed BulkIO input Port to set sriChanged flag and register default SRI for unknown stream IDs in pushPacket.
* Modified Valgrind support in Device Manager to avoid attempting to overwrite the Device executable file with the Valgrind log file.
* Improved unit test for Components.

### IDE Changes
* Removed Subversive (Subversion) from the IDE.

### REDHAWK Basic Components Fixes
* DataConverter fixed floating point error in conversion from complex to scalar.
* DataConverter removed an unused variable.
* DataConverter fixed conversions from float and double to char and updated corresponding unit tests.
* DataConverter updated to have a distinct unit test for each test case.
* fcalc added error checking and recovery to property configuration.
* FileReader updated to not use Domain Manager when in Sandbox.
* FileWriter updated to not use Domain Manager until configured/initialized.
* FileWriter fixed to write file to correct location when launched in a Domain.
* psd updated to pass keywords COL_RF and CHAN_RF.
* psd updated unit tests to check precision and accuracy.
* SigGen updated to use unsigned types where appropriate.
* SigGen updated to have increased precision in all implementations.
* SigGen updated to only initialize timestamps when started.
* SigGen C++ implementation updated to be more responsive to configuration calls.
* SigGen C++ implementation updated delta_phase calculation to be consistent with other implementations.
* SigGen updated to send EOS when configured with new stream_id.
* RBDSDecoder updated to include RBDS messages in the log.
* TuneFilterDecimate fixed unit test tearDown function to clean up properly.

### REDHAWK Basic Devices Fixes
* RTL2832U updated to include report of FEI compliance test results.
* USRP_UHD updated unit test default configuration to use UHD version that comes with REDHAWK.
REDHAWK Shared Libraries

### REDHAWK Shared Libraries Fixes
* RedhawkDevUtils updated float/double byte-swap methods to not cast to anything but char*.

### REDHAWK Device Dependencies Fixes
* librtlsdr corrected dependency listed in README.md.
* librtlsdr corrected install location of udev rules from source build.

### Documentation Improvements/Fixes
* Removed recycle from the the REDHAWK Overview.
* Updated Core Asset names with namespaces.
* Updated GPP description now that it is written in C++.
* Clarified Property types.
* Improved language discussing primitive types available for Properties.
* Corrected description of Device library dependencies.
* Simplified description of recommended packages to install.
* Improved information regarding adding a library in Makefile.am.
* Added explanation of the PrecisionUTCTime structure and moved description of the SRI structure to the section where SRI is discussed.
* Updated capacity allocation information to explain automatic capacity allocation.
* Added description of SRI keywords used with FEI Devices.
* Added Valgrind information in GPP and Device Manager sections.
* Added information regarding the use of raw_input() in Python Sandbox.
* Added information about new GPP reservation floor.
* Added version 1.10.X in upgrading information.
* Updated installing system dependencies REDHAWK version to 2.01.
* Added information about Timestamp Helper Methods.
* Added C++ property query and configure callbacks information.
* Added getCurrentStream() information in BulkIO stream documentation.
* Updated C++ property listener examples to use 2.0-style methods.
* Added information to correct omniNames/omniEvents install order on Ubuntu.
* Added information about deprecated properties upgrade process.
* Added setuptools to the install for Ubuntu.
