# Eclipse Smarthome Packaging Sample
<img src="https://www.eclipse.org/concierge/images/logo.png" alt="concierge osgi" width="200"/>

This repository contains a sample which runs eclipse smarthome withing an concierge OSGi container. It should show
how easy a own smarthome distribution can be packaged.

Additionally, you can use this example to build an own minimal distribution with an very optimized memory footprint.

1. Prerequisites - Install Maven
================
Please use the instructions on main project's readme to install maven: https://github.com/eclipse/smarthome#1-prerequisites
Make sure **mvn** command is available on your path.

2. Checkout
================
Checkout the source code from GitHub, e.g. by running:

```
git clone https://github.com/eclipse/smarthome-packaging-sample.git
```

3. Build the distribution
================
Run
```
mvn clean install
```

The maven build will create an ZIP file with all required components like
* the concierge runtime
* eclipse smarthome bundles
* 3rd party bundles
* start scripts

You can find the created distribution under **/target/smarthome-packaging-sample-[version].zip**

4. Start runtime
================
TBD


Customize the distribution
================
## Concierge configuration with XARGS file
TBD

## Change the OSGi Shell
The sample does already include two versions of osgi shell implementations:
 * Concierge Shell (default)
 * Apache Felix GoGo
 
If you want using Apache Felix GoGo simple uncomment the GoGo bundles and remove startup of concierge shell 
like:
```
# -istart ${concierge.dir}/org.eclipse.concierge.shell-${concierge.version}*.jar
-istart ${system.dir}/org.apache.felix.gogo.runtime-0.*.jar
-istart ${system.dir}/org.apache.felix.gogo.command-0.*.jar
-istart ${system.dir}/org.apache.felix.gogo.shell-0.*.jar
```

At next startup you will see the **g!** prompt instead of **concierge>**

