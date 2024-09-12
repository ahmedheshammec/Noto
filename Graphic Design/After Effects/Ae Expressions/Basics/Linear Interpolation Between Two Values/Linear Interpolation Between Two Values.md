Let's Say We Have the Following Line Rotating 360 Degrees
![image](7A5D579B-EEEB-4FE9-84C0-5DE8641ACA1F.gif)￼
❖ And We Want to Reveal a Background Behind the Line and the Reveal Will Happen with the Rotation of the Line.
❖ First We Will Use the Effect Radial Wipe Cuz It Gives the Same Effect as the Rotation
❖ But How We Gonna Align the Rotation Value (in Degrees) with the Transition Completion of the Radial Wipe (in Percentage)? The Answer Is the Linear Interpolation And We Won't Even Need Keyframes
❖ Apply the Radial Wipe Effect to the Current Background and Set the Wipe Center to the Start of the Line as Follows:
![image](7C4A3191-535C-4D94-B14F-8AAC05B9F477.jpg)￼
❖ And Next We Will Add the Linear Interpolation as Follows:
![image](72AB05A0-5F30-4E45-8134-02567196ABD3.gif)￼
❖ So We're Interpolating the Value Between 0 and 360 of the Rotation to the Value Between 0 and 100 of the Transition Completion
❖ Final Result:
![image](FDF10E52-F2C0-4779-B177-F916FD6B2F05.gif)￼

