# NS3_Wave


Introduction: 
      
      - ns-3 is a discrete-event network simulator for Internet systems, targeted 
        primarily for research and educational use. ns-3 is free, open-source software, licensed 
        under the GNU GPLv2 license, and maintained by a worldwide community.
        
Implementation steps:

      1- Create 3 vehicles nodes.
      
      2- The vehicles are mobile on a rectangular area according to RandomWalk2dMobility 
          model:
          
              •The area is a rectangle with bounds 0<x<500 and 0<y<500. 
              •The speed of the vehicles is a uniform random number between 8 m/s and 13 m/s. 
              •Vehicles are initially positioned randomly on the rectangular area. 
              
       3- Set the data link type of PCAP traces to be used. 
          This function has to be called before EnablePcap(), 
          so that the header of the pcap file can be written correctly. 
          Here we set it to IEEE 802.11 Wireless LAN headers.
          
          
        4- At second1, vehicle1(vehicle with index 0) sends a broadcast message (wave short 
           message) via control channel (CCH):
           
                    •The packet payload of the CCH message is 500 Bytes.
                    
                    •The ethernet type protocol is set to 0x88dc which correspond to WSMP.
                    
                    •The transmission charact eristics of this CCH broadcast message are as follows:
                    
                                - The transmission data rate (wifiMode) is OfdmRate12MbpsBW10MHz.
                                
                                - The priority of packets is 7(the packets priority is a number between 0 and 7, 
                                and 7 is the lowest priority)
                                
                                - Replace the constants to be variables that we would pass to the “SendOneWsmpPacket” 
                                function.

         5-  At intervals of 5 seconds (5, 10, 15, 20), vehicle 1, vehicle2 and vehicle 3 broadcast messages
            of size 1000 bytes via service channel 1 (SCH1):
            
                  •The priority of the packets sent from vehicle 1 is 0 (highest priority)
                  
                  •The rate of the broadcast for vehicle 1 is 27Mbps.
                  
                  •The priority of the packets sent from vehicle 2 is 5.
                  
                  •The rate of the broadcast for vehicle 2 is 9Mbps.
                  
                  •The priority of the packets sent from vehicle 3is 7.
                  
                  •The rate of the broadcast for vehicle 3is 6 Mbps.
