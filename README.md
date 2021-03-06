# Vicon2WorldViz
Example code to stream Vicon Nexus data into WorldViz

As of 5/2/2016, there is no supported or other opensource method of streaming motion data from Vicon's Nexus software to WorldViz. The purpose of this repository is to share an opensource method for doing so (TCP).

Method:
  Using the Vicon SDK a c++ server application relays frame data to a multi-threaded python application that updates Vizard in "real" time. The c++ application in this example reformats frame data into xml or comma delimited string for serialization to the Vizard client. 
  
Unfortunately I cannot post an executable, since I legally can't re-distrubte the Vicon SDK...
  
Requirements:
  - Windows 7 (not sure if this works in other Windows or MacOS)
  - Vicon Nexus 1.8.5 or 2.x
  - Vicon SDK 1.5 or newer (64 bit in this example)
  - Vizard 4 or above (not sure about earlier versions)
  - c++ compiler (Visual Studio 13 v12 used here)

Notes:
  - There are two versions, one where the majority of important data is formatted into an xml string and sent to the client. The xml serialization is not a requirement, just a design choice (human readable and easy to see what is going on). In real-life I don't use the xml because the size of the packets can slow down the communication speed. The other example does not use xml, but simply creates a comma delimited string.
  
  - Depending on your PC's specs you may get a different speed performance. Using SDK 1.5 I've experienced frame drops, not becuase of anything this code does but because Windows is not a real time OS. Vicon recently sent me SDK 1.5.1.74865h which is capable of sending 100% of the frames (by using a buffer) but no garuntee of speed in updating the Vizard window. In other words, if there is a 50 frame delay you might see the Vizard window do a "catch up" where the motions look they are being fast-forwarded. 

Background:

  Our laboratory, the Human Movement Research Laboratory (HMRL) at the University of Pittsburgh http://www.engineering.pitt.edu/MARGroup/ is starting to use virtual reality (VR) as a possible intervention method to rehabilitate patients with neurological disorders (i.e. stroke). The lab captures human motion data with a Vicon Nexus system, and then updates a VR (WorldViz) display to provide "biofeedback" on their performance. 

  WorldViz is a virtual reality software program that can update objects and animate avatars in a VR world in real time, provided the motions can be provided by some program or motion capture system. WorldViz currently runs on Python, and is executed through a Python program called Vizard. 
  
  Vicon Nexus is a motion capture program that can track passive-reflective markers worn by human subjects in real time. The main benefit of Nexus (i.e. as opposed to Tracker which has a supported method of streaming data to Vizard) is that it can track segments attached to non-rigid bodies. Since human subjects are not rigid objects like a brick, markers that form a local coordinate system can deform a lot, making it difficult to keep track of a body segment. Hence, Nexus is the only program we can use to track human motion well enough to provide accurate biofeedback.
  
Sentiment:

  I have shared this code because I enjoy programming and I have greatly benefited from others who have shared their work. I also like to share because the feedback can make me a better programmer. Also, there may be others who are looking to do something like this and it might help them too.
  
