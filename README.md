# Syringe-extruder

A toolhead for printing with paste using an Ender printer, like model 3 or 5.

<img src="/imgs/s1.png" width="400">

<img src="/imgs/s2.png" width="400">

<img src="/imgs/s3.png" width="400">

# Design

The idea was to hack a 3D printer to mount the toolhead as easy as possible. It uses the same extruder motor of the printer, but there are some tweaks that must be done in the hardware, firmware and slicer software. All the pieces are [HERE](https://grabcad.com/library/syringe-hydraulic-paste-extruder-for-ender-1) and the parts list [HERE](PARTS.md).

The extruder pushes a syringe that is conected with a tube to another syringe on the gantry. The syringe pushes water into the other syringe, so the plunger moves downward. This plunger pushes the plunger of other syringe that holds the material, wich is extruded trough the tip. 

The extruder motor is connected to a pulley and a timing belt, to increase torque. A bigger pulley is connected to the power screw to move the carriage that pushes the plunger of the syringe. There is a pair of linear bearings that moves through 8 mm rods. 

The luer lock syringes are connected using 2 3-way luer valves. A 3d printed nozzle can be mounted in the tip of the material syringe.


# Fabrication

Most of the parts were 3d printed in PLA. The T-Slots were cutted with saw and the rectified with a cnc mill.

<img src="/imgs/s9.png" width="400">

# Assembly

You have to remove the extruder and the extruder motor assembly completely from the printer, EXCEPT for the thermocouple. The connector of the extruder motor is connected to the syringe extruder. The syringe toolhead fits in the two extrusions of the gantry with M3 thread.

I grounded the extruder to an Ender 5 using 2020 angle brackets between the T-slots.

The water filling of the syringes could be tricky, the idea is that the hose, the extruder syringe and the tip (not the full body) of the toolhead syringe should be full of water. If there is air in between, the compression of it could lead to undesired results.

# Tweaks

Hardware: The z zero reference is obviously going to change depending on the syringe and the nozzle. I put a t-slot to move the sensor up and down with a t-nut.

Firmware: The step per mm in the E axis should change. In my case, using a 1:3 reduction instead of the 1:3.75 of the CAD design, the number is 1191 steps approximately. 

Software: I use the printer with the monitor of Cura, as a new custom machine. The nozzle should be the size of the tip of your syringe. Everything else should be the default settings of the printer that you are using. There is a problem with creating a new material with the inner diameter of the syringe, so I am reducing the flow to 1% in the settings. 

Before printing: The instruction M302 S0 has to be sent to allow cold extrusion. Then, after loading the syringe with material into the toolhead, you have to move the E axis until the plungers are touching each other. 

# Tests

I made a few printings, some with silicone and others with some cheap clay, using different syringe diamaters (3.9 mm for clay. 2.8 mm for silicone). There are a couple of images in the imgs/test folder.

# Future work

- One or Two endstop switches should be added to limit the stroke of the syringe.
- Maybe fan or heaters will help when printing some materials.

# Comments

- I only played with this machines like 3 days.
- It is a dirty process.
- There is some compactation before extrusion.
- After extruding some material, it will flow anyway during some time, because of the built up pressure inside the syringe. Finding the right material is very important.
