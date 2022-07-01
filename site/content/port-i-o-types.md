+++
date = 2022-06-09T11:45:46Z
hiddenFromHomePage = false
postMetaInFooter = false
title = "Port I/O Types"
[flowchartDiagrams]
enable = false
options = ""
[sequenceDiagrams]
enable = false
options = ""

+++
# Pass by Value

* `ap_none`: No I/O protocol. This is the default for inputs.
* `ap_stable`: No I/O protocol.
* `ap_ack`: Implemented with an associated output acknowledge port.
* `ap_vld`: Implemented with an associated input valid port.
* `ap_hs`: Implemented with both input valid and output acknowledge ports.

***

# Pass by Reference

* `ap_none`: No I/O protocol. This is the default for inputs.
* `ap_stable`: No I/O protocol.
* `ap_ack`: Implemented with an associated input acknowledge port.
* `ap_vld`: Implemented with an associated output valid port. This is the default for outputs.
* `ap_ovld`: Implemented with an associated output valid port (no valid port  
  for the input part of any inout ports).
* `ap_hs`: Implemented with both input valid port and output acknowledge  
  ports
* `ap_fifo`: A FIFO interface with associated output write and input FIFO full ports.
* `ap_bus`: A Vivado HLS bus interface protocol.