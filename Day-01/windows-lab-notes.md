Explore Windows Event Viewer
Step 1: Open Event Viewer

Press Win + R, enter eventvwr.msc, and press Enter.

Step 2: Inspect System logs

Open Windows Logs → System. Select a recent entry and examine its General and Details tabs.

Step 3: Inspect Security logs

Open Windows Logs → Security, if accessible. Review available event records without changing audit policies or clearing logs. Access may require administrator privileges.

For every event I have inspected, recorded these fields:
- Timestamp: When did it happen?
- Event ID: Which type of event was recorded?
- Source: Which component recorded it?
- Level: Information, Warning, Error, or another available level.
- Message: What actually happened?

SOC thinking: A single failed logon is not proof of an attack. Repeated failures against one or more accounts, unusual source addresses, and subsequent successful logons may provide stronger evidence