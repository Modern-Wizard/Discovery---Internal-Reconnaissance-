# Discovery-Internal Reconnaissance

## Internal Reconnaissance
Based on the collected findings, we have discovered that the malicious binary continuously uses the C2 traffic:

    We can easily decode the encoded string in the network traffic.
    The traffic contains the command and output executed by the attacker.

## Investigation Guide
To continue with the investigation, we may focus on the following information:

    Find network and process events connecting to the malicious domain.
    Find network events that contain an encoded command.
    We can use Brim to filter all packets containing the encoded string.
    Look for endpoint enumeration commands since the attacker is already inside the machine.

In addition, we may refer to our cheatsheet for Brim to quickly investigate the encoded traffic with the following filters:

    To get all HTTP requests related to the malicious C2 traffic: _path=="http" "<replace domain>" id.resp_p==<replace port> | cut ts, host, id.resp_p, uri | sort ts

Significant Data Sources:

    Packet Capture
    Sysmon
