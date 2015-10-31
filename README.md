# ovsdriver
Nodejs OpenVSwitch utility wrapper , provides the API for OpenVSwitch operations.     


Currently it supports the following OpenVSwitch functionalities             

1. Create a Bridge              
2. Add Interface to the Bridge           
3. Set the SDN Controller IP to the Bridge            
4. Set the Openflow protocol version to the Bridge             
5. Set the Datapath id to the Bridge              
6. Enable the Bridge                
7. Disable the Bridge               
8. Delete the Bridge              
9. Get the Status of the Bridge                  

       
## API Details :        


All the API returns true on success case , false on failure case.

1. createBridge : (bridgname, callback)               
    bridgename is the input. Example "switch1"              


2. addInterface : (bridgname,ifname,callback)              
    bridgename and ifname is the input. Example ifname is "veth1"         


3. setController : (bridgename , controllerip, callback)        
    controller IP should be in full format protocol:<ip>:portnumber                      
    Example:  "tcp:0.0.0.0:6633"      

4. setOFVersion: (bridgename, versionno, callback)          
    versionno should be in 1.0 or 1.1 or 1.2 or 1.3       

5. setDPid : (bridgename,dpid, callback)            
    dpid should be 16digit.         
    Example = "0000000000000001"          


6. enableBridge : (bridgname, callback)         
7. disableBridge : (bridgname , callback)         
8. deleteBridge : (bridgename, callback)             
9. getStatus: (bridgename, callback)           
    returns "running" or "notrunning"          



## Program Example 
written in coffeescript.         
This is just indicative program to demonstrate functionality . It cannot run as it is.         


        ovs = require('ovsdriver')
        ovs.createBridge "sw1", (result) =>
            util.log "Bridge creation " + result                               
        ovs.addInterface "sw1", "veth1",(result) =>
            util.log "AddInterface result", result


This driver is used in Kaanalnet application to manage ovs, 
https://github.com/sureshkvl/kaanalnet/blob/master/src/builder/switchCtrl.coffee






