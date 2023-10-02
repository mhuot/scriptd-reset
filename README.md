# scriptd-reset
This is an OpenNMS scriptd beanshell to check an SNMP value vs metadata

Here is the snippet needed to be added to the scriptd-configuration.xml. I keep them in $OPENNMS_HOME/scriptd-bsh.d

```
    <start-script language="beanshell">
        log = bsf.lookupBean("log");
        source("$OPENNMS_HOME/etc/scriptd-bsh.d/scriptd-utils.bsh");
    </start-script>
    <event-script language="beanshell">
        <uei name="uei.opennms.org/scriptd/reset"/>
        source("$OPENNMS_HOME/etc/scriptd-bsh.d/scriptd-reset.bsh");
        event = bsf.lookupBean("event");
        node = bsf.lookupBean("node");
        processReset(event, node);
    </event-script>
```
