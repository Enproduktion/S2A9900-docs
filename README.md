# S2A9900 Documentation

S2A9900 documentation, based on the HELP output of the S2A9900 terminal commands.

## Connect to S2A9900

1. Connect yourself to the RJ45 telnet plug (right above the RJ45 LINK connector)
2. `telnet <IP>`
3. default user: admin
4. default password: password

## Howtos

### Recover failed state in a dual mode

if DUAL shows failed for the first node, do:

```bash
DUAL SINGLET
DUAL HEAL
```

if DUAL shows failed for the second node, do:

```bash
DUAL HEAL
```

### Graceful shutdown

1. Connect to device 2
2. `SHUTDOWN`
3. Connect to device 1
4. `SHUTDOWN`
