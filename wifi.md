# WiFi
Link: [https://www.youtube.com/watch?v=RSq4nY8QdG8](https://www.youtube.com/watch?v=RSq4nY8QdG8)

Commercial name for 802.11

## BSS (Basic sevice set)
1. `Ad-hoc`: Devices which can talk to one another in ad hoc manner.
2. `Infrastructure`: With access point

## DCF and PCF
- DCF for contention based services
- PCF sits on DCF for contention free services

## CSMA/CA (DCF)
Carrier sensing multiple access / Collision avoidance

1. CD cannot happen as we don't have full duplex connection. WiFi is half duplex.
2. Signal strength may not be high enough for collision detection.
3. Hidden terminal problem

```
Source                  Reciever
    (if found some issues)
Wait
DIFS
time

----------- RTS (req to send) ->
<-- CTS (Clear to send) -------

SIFS
time

------------- Data ----------->
                        SIFS
                        time
<--- ACK ---------------------
```
 When sending RTS, start a timer. If CTS is not got back within, increase backoff time and backoff.

**Note**: RTS has a duration channel which tells how much time is supposed to be taken. This is called `NAV: Network allocation vector`

## Hidden terminal problem
Assume the following:

```
B        A          C
```
B may not know where C is and vice versa.

This is solved by CSMA/CA.

## Exposed station problem
Station is not able to send the data even when channel is idle.

Assume the following:
```

R1 <--- data tr --> S1                    S2 <--- wants to connect ----> R2

Signals:
---------R1----------
--------------------------S1---------------
                    ----------------------S2-------------------------------
                                           ---------------R2---------------
```
S1 is communicating with R1 and S2 wants to communicate to R2.
So S2 will try sensing the channel and will see interfernce and assume the channel is being used.
However his signals cannot interfere with S1<--> R1 path.

**How to solve it?**
1. When S1 wants to talk to R1, it will send an `RTS` signal which both R1 and S2 will hear.
2. When R1 responds to the signal with `CTS`, it will only reach till S1 and not S2. Keeping this log at S2 will help us identify if it's a exposed station problem.

## 802.11 a/b/g/n/ac

### a
54Mbps = 6.75MB
2Ghz
25ft

### b
11Mbps
2.4Ghz
100ft
Slower than 802.11a 54 - 11 Mbps
Other things like baby monitor would interfere with 2.4Ghz

### g
54Mbps
2.4Ghz - backwards compatibility with 802.11b
100ft

### n
300 - 600 Mbps
MIMO - Multiple input / Multiple output
2.4 / 5 Ghz
150ft

### ac
400 Mbps - 1 Gbps
8 antenna ( 4 on n )
5Ghz ( 2.4Ghz available using 802.11n )
Beam forming
Not backwards compatibility 

### 802.11ax (WiFi 6)
2.4 - 14 Gbps (multiple stream)
OFDM (Orthogonal Frequency-Division Multiplexing)
BSS coloring
2.4 and 5 Ghz
Multi user MIMO (8 streams)
TwT (Target Wakeup time)
