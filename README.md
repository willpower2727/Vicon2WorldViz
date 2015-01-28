# Vicon2WorldViz
Example code to stream Vicon Nexus data into WorldViz

As of 1/28/2015, there is no supported or opensource method of streaming motion data from Vicon's Nexus software to WorldViz. The purpose of this project is to share an opensource method for doing so.

Background:

  Our laboratory, the Human Movement Research Laboratory (HMRL) at the University of Pittsburgh, is starting to use virtual reality (VR) as a possible intervention method to rehab patients with movement disorders (i.e. stroke). The lab captures human motion data with a Vicon Nexus system, and then updates a VR (WorldViz) display to help provide "biofeedback" on their performance. 

  WorldViz is a virtual reality software program that can update objects and animate avatars in a VR world in real time, provided the motions can be provided by some program or motion capture system. WorldViz currently runs on Python, and is executed through a Python program called Vizard. 
  
  Vicon Nexus 1.8.5 is a motion capture program that can track reflective markers worn by subjects in real time. The main benefit of Nexus (as opposed to Tracker) is that it can track markers attached to non-rigid bodies. Since human subjects are not rigid objects like a brick, markers that form a local coordinate system can deform, making it difficult to keep track of a body segment. Hence, Nexus is the only program we can use to track human motion.
  
Problem:
  
  There is no current method to stream Nexus data into WorldViz. 
  
Solution Method:

  This project contains example code to stream Nexus data into WorldViz using this method:
  
  1) a C++ server application is defined using ViconSDK API that can obtain Nexus data, and then relay that data to a Python client via xml serialization (tinyXML)
  
  2) the Python client updates the VR world
  
Requirements:

  1) Vicon Nexus
  2) WorldViz and Vizard
  3) ViconSDK 
  4) cpp compiler
  
Notes:

  I have shared this code because I enjoy programming and I have greatly benefited from others who have shared their work. I also like to share because the feedback can make me a wiser programmer. Also, there may be a few others who are looking to do something like this and it might help them too.
  
