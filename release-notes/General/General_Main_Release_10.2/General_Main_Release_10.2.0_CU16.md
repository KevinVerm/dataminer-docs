---
uid: General_Main_Release_10.2.0_CU16
---

# General Main Release 10.2.0 CU16 – Preview

> [!IMPORTANT]
> We are still working on this release. Some release notes may still be modified or moved to a later release. Check back soon for updates!

> [!TIP]
> For information on how to upgrade DataMiner, see [Upgrading a DataMiner Agent](xref:Upgrading_a_DataMiner_Agent).

### Enhancements

#### System Center: Overhaul of LDAP settings [ID_35782]

<!-- MR 10.2.0 [CU16]/10.3.0 [CU4] - FR 10.3.6 -->

In *System Center > System settings > LDAP*, you can configure a number of LDAP settings. These settings have had an overhaul.

- In the *General* tab, from now on, you will only be able to set *Authentication type* to either "Anonymous" or "Simple".

  > [!NOTE]
  > When you set *Authentication type* to "Anonymous", the *User name* and *Password* fields will now be disabled. When both fields contain a value, *Authentication type* will by default be set to "Simple".

- In this section, it is now also possible to configure the *nonDomainLDAP* setting. Up to now, this setting could only be configured in the *DataMiner.xml* file.

- When you update LDAP settings, a warning will now appear to notify you that these settings will only be changed on the DataMiner Agent to which you are connected. Changes made to LDAP settings will not be synchronized among the agents in the cluster.

Also, a number of issues have been fixed. Up to now, the value entered in *Use fully qualified domain name (FQDN)* would not be saved to the *DataMiner.xml* file, an incorrect default value would be entered in the *User class name* field, and the value entered in the *Password* field would get lost when the LDAP settings were updated without changing the password.

#### Failover: Obsolete CheckVIPs thread has been removed [ID_36253]

<!-- MR 10.2.0 [CU16]/10.3.0 [CU4] - FR 10.3.7 -->

In Failover setups using virtual IP addresses, once every minute the CheckVIPs thread would check whether the online Agent holds the correct IP addresses. However, due to the many locks it claimed to verify the current state of the IP addresses, it would delay other actions being executed in the system.

This obsolete thread has now been removed.

### Fixes

#### Cassandra Cluster: Every DMA would incorrectly try to delete any possible old Cassandra compaction and repair tasks found in the entire DMS [ID_31923]

<!-- MR 10.2.0 [CU16]/10.3.0 [CU3] - FR 10.3.3 -->

At start-up, every DataMiner Agent with a Cassandra Cluster configuration would incorrectly try to delete any possible old Cassandra compaction and repair tasks found in the entire DMS.

From now on, at start-up, every DataMiner Agent with a Cassandra Cluster configuration will only delete the old Cassandra compaction and repair tasks found locally.

#### DataMiner Cube - Resources app: Problem when opening the element list in the 'device' tab [ID_36239]

<!-- MR 10.2.0 [CU16]/10.3.0 [CU4] - FR 10.3.7 -->

When, in the *Resources* app, you created a resource and then opened the element list in the *device* tab in order to link a device to that newly created resource, in some cases, DataMiner Cube could become unresponsive, especially when the element list contained a large number of elements.

#### Business Intelligence: Secondary index of certain SLA logger tables would not be created correctly [ID_36245]

<!-- MR 10.2.0 [CU16]/10.3.0 [CU4] - FR 10.3.7 -->

The secondary index of certain SLA logger tables would not be created correctly. As a result, certain rows in those tables would not get cleaned up and exceptions like the following would be added to the *SLDBConnection.txt* log file:

```txt
SLDataGateway.Types.DBGatewayException: CassandraConnection ExecuteQuery - exception while executing query: SELECT "array_active_service_alarms_id","array_active_service_alarms_time" FROM ELEMENTDATA_7102_1334_750 WHERE "array_active_service_alarms_rootid" = '0/0'; - Cannot execute this query as it might involve data filtering and thus may have unpredictable performance. If you want to execute this query despite the performance unpredictability, use ALLOW FILTERING
```

When SLAs were stored in a Cassandra cluster, none of their rows would get cleaned up.

#### Dashboards app & Low-Code Apps: State component would incorrectly not be cleared when its input feed was cleared [ID_36261]

<!-- MR 10.2.0 [CU16]/10.3.0 [CU4] - FR 10.3.7 -->

In some cases, a *State* component would incorrectly not be cleared when its input feed was cleared.

#### Low-Code Apps: Table actions would incorrectly be executed before the rows were fed [ID_36263]

<!-- MR 10.2.0 [CU16]/10.3.0 [CU4] - FR 10.3.7 -->

In some cases, table actions would be executed before the rows were fed. As a result, the feed would get lost when you navigated away from the page via an action. From now on, a row will always be fed before row actions are executed.

#### Dashboards app: Height of 'DATA USED IN DASHBOARD' section would incorrectly change after collapsing and expanding it [ID_36282]

<!-- MR 10.2.0 [CU16]/10.3.0 [CU4] - FR 10.3.7 -->

When you collapsed and expanded the *DATA USED IN DASHBOARD* section of the *DATA* tab, in some cases, the height of that section would incorrectly change.

#### Monitoring app: Surveyor items would be sorted incorrectly [ID_36303]

<!-- MR 10.2.0 [CU16]/10.3.0 [CU4] - FR 10.3.7 -->

In the Surveyor of the Monitoring app, items of which the name contained a number would be sorted incorrectly. For example, *Element 2* would appear below *Element 11*. From now on, the items in the Surveyor of the Monitoring app will be sorted in the same way as those in the Surveyor of DataMiner Cube.

#### DataMiner Cube - Visual Overview: Problem when opening an EPM card [ID_36323]

<!-- MR 10.2.0 [CU16]/10.3.0 [CU4] - FR 10.3.7 -->

When you opened an EPM card by clicking a shape that was linked to the EPM object via the *SystemName* and *SystemType* properties, in some cases, the card would be missing certain pages.