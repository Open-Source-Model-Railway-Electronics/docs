# Make your own custom wire split

Though there are a million ways to make your own wire splits. How cool would it be if you can make your own customized PCB for it? A split that exactly furfills your needs. This page explains how you can design your own wire split PCB's. I will show various variations.

This guide follows up on this [this guide](https://github.com/Open-Source-Model-Railway-Electronics/docs/tree/master/makeYourOwnCustomLedStrip.md) where the basics of KiCad are explained.

## Step 1, setup a project
In this example we are gonna make an 8 pole split that carries 2 DCC lines, 12V + GND, 2 PWM lines and 5V + GND. So open KiCad and click file -> New Project. Find a location on your system like your Documents folder, enter an apropiate file name and click save. 

![ ](image.png)

## Step 2, make a schematic

Open the schematic editor by clicking on it's symbol. In this example we will be using 8 pole screw terminals that we want to split 4 ways. So the first thing we are gonna to is to add 8 pole screw terminals. In the schematic editor press the 'a' key and enter "screw terminal" in the search bar. Click the 01x08 one and click OK. You can also double click on the 01x08 screw terminal. Place the screw terminal somewhere in the schematic.

![](image-1.png)

We need four of them, so select it, and copy (Ctrl C) paste (Ctrl V) it 3 times.

![](image-2.png)

Arange and rotate the screw terminals to a logical position. I will put them in a rectangular formation. But you can essentially do any formation you want. This is only the schematic and it does not really affect how the board will look like.

![](image-3.png)

Next we need to make the connextion. Hover the mouse about one of the connection points, and press the 'w' key to start a wire. You can also simply click on the connection node.

![](image-4.png)

Connect all the wires in a logical order between the screw terminals. 

![](image-5.png)

We also need to connect the horizontal and vertical lines.

![](image-6.png)

Place 8 of these junctions like this.

![](image-7.png)

What is also really important, add labels to the wires. The connections are valid, but we want to use names. This essentially lets us see better what we are doing when we are making the board. So press the 'L' key start placing well named labels

![](image-23.png)

Lastly. We will also add mounting holes to the schematic. Strictly you don't have to do this here, but it is an option. So press 'a' and search for a mounting hole.

![](image-8.png)

Place 4 of them

![](image-9.png)

## Step 3, select components.

Open u the assign footprint menu from the top toolbar. In this menu we need to look for footprints. The filters will help you alot. If you select one of the mounting holes, you will already see mounting holes. I typically use M3 holes, but you are free to pick any of the list.

![](image-10.png)

Concerning the screw terminals. There are many. Different sizes, forms, systems. I usually use 3.5mm screw terminals. So I'll use this now as well. In order to find good ones, I enter 3.5 in the search bar. This narrows the choise to 3 options. I always use the one of Phoenix because I happen to know they come with 3D models.

When you are ready, you can click OK.

![](image-11.png)

## Step 4, Make the board

Open up the board editor by clicking on the board editor button. When it is open press F8 key and hit 'update PCB'. This will update the board with the components in our schematic. The items are slaved to the mouse cursor. So find an empty spot and left click to commit the location.

![](image-12.png)

Now we need to arrange the components. In order to do this, I recommend to use a grid size of 0.5mm

![](image-13.png)

Now zoom in and place the components as taught in the previous tutorial. You can open the 3D viewer from time to time with alt + 3. I can imagine that the orientation of the screw terminals are difficult to see.

![](image-16.png)

![](image-14.png)

We also draw a rectangle in the edge cuts layer. In our example a size of 50x50mm seems good. Than move the components so everything fits nice in the box.
Use the big cross hair to allign the screwterminals properly.



What you can can do, is move the screw terminals a little inside so we get more space for the silk texts. We will add those later on

![](image-15.png)

Now I turn off the Fab layers to remove unneeded and unvisable texts. 

We need to place tracks now. Hover over any of the screw terminal's pads and press 'x' to start a track. You will notice that the connections are crossed. It could be that this is desirable. You can for instance rotate the PCB 180 degrees and the connections would be the same. But for the sake of placing the tracks it would be easier if our tracks could be straight. 

![](image-18.png)

So we go back to the schematic, move a screw terminal (J2 and J3) and then we flip the component with the x key.
You will now see, that Pin 1 is aligned with pin 8 of the opposite side. This is what we want.

![](image-20.png)

Now go back to the board and press F8 key to update the PCB again with the schematic changes

![](image-21.png)

N.B. Make sure that the place of the schematic symbols and the place of the board foot prints are the same. Meaning that J1 is opposite to J3 and J2 is opposite to J4. Otherwise you will things slightly more difficult for your self.

This is want we want to see. We can now set all traces. The easiest what we can do is to place horizontal lines on the top layer and the vertical lines on the bottom lines.
![](image-22.png)

 As we want this split to handle currents of like 3A or so, we can and will use 1mm thick wires. In the top left side you can set the track size. But you need to add the size first. You can do so by clicking on the edit pre-defined sizes.

![](image-24.png)

Now place all traces. Do not place the traces for the GND pads. With V you can place the traces on the other side.
![](image-25.png)

![](image-26.png)

For the GND connection, we will use a filled copper zone. So select either the F.cu or B.cu layer on the right, click the add filled zone button and click a starting point. Take a point outside the PCB in a corner somewhere. This will open a menu. You need to select both layers and the GND net and Press OK. You now also need to place the remaining points.  This does not have to be neat, you just need to make a box where the PCB can fit in entirely

![](image-27.png)

![ ](image-28.png)

The last corner is placed on top the the begin corner, this finishes the zone. Press B when you are finished. This will update the zones.

![](image-29.png)

We also need to connect the horizonal and vertical lines. We will do so with via's. Click the via button on the right and place via's where the tracks of the same net intersect. Of you click on a wrong intersection you will get a warning

![](image-30.png)

![](image-31.png)

We also do good if we connect the GND planes on more placed with some vias. Place vias on some points to interconnect both ground planes.

![](image-32.png)

Lastly we need to add some texts on the PCB so we can see where which wire goes. We can also removed the mounting hole texts. The J1 and J4 are also not really needed, might as well get rid of those to. So click them, and press the delete.

To add a text, first select the front Silk layer, and then click on the text button. You also would do good in this case to reduce the size to 50%.

![](image-34.png)

If you copy and paste a text, you also copy the sizes. Then you only have to change the text. You can now also see why we added labels in the schematic. You can now see which connections are ment for DCC for instance. So go place all the texts on your board. Also check the 3D model from time to time

![](image-35.png)

When you are content with your board. You can add OSHW symbol in silk layer. This is as simple as adding a foot print

![ ](image-36.png)

And voila! Your own customized board design is ready. Now it is just a matter of plotting gerber files and making the order as is described in the previous tutorial.
![](image-37.png)