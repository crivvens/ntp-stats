# ntp-stats
Stats script and webpages for the Farnham NTP Server

Original scripts by Leo Bodnar - 25th August 2016

## Installation

### Dependencies

* rrdtool >= 1.6.0
* imagemagick

### Create new rrd file
```
rrdtool create ntp1.rrd \
  --start now-2h --step 1s \
  DS:req:GAUGE:5m:0:120000 \
  RRA:AVERAGE:0.5:1s:10d \
  RRA:AVERAGE:0.5:1m:90d \
  RRA:AVERAGE:0.5:1h:18M \
  RRA:AVERAGE:0.5:1d:10y
  ```
### Install upstart service files (Ubuntu 14.04)

1. Modify leontp.conf,leoimages.conf for correct path
2. Copy leontp.conf,leoimages.conf to /etc/init/
3. `sudo start leontp && sudo start leoimages`
