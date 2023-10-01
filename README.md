# Monitor Addons
Expand the experience with custom monitors to add to your tractors and other vehicles for FS22. 
## Information

The Monitor Addon Pack from Lazy E Modding currently includes:
- John Deere BaleTrak Monitor
- Intercomp Weight Monitor

This addon Pack is more of a prefab than a mod and should be treated as such. To make this pack work you’ll need to follow the instructions provided. **Lazy E Modding will not provide support for installing the monitors** as it’s intended to be done by modders who know how to install a simple edit without needing to be walked through step by step. 

## Installation instructions
### Step 1: Downloading Dashboard Live
Download [DBL from Modhub](https://www.farming-simulator.com/mod.php?lang=en&country=us&mod_id=264698&title=fs2022), or a development version from [GitHub](https://github.com/jason0611/FS22_DashboardLive)
### Step 2: Downloading Assets
Download the [Release Assets]() from this GitHub Repo.
### Step 3: Adding to the i3d 
Position the monitors included in the release package into your vehicle in Giant’s Editor. If you’d like to put them on a mount, you’ll have to add them yourself as no mounts are included in the release package. The clamps on the back of the monitors are intended to use 0.75” (19mm) diameter poles. Make sure to copy and paste the textures folder from the bale monitor into the mod that you are editing, and make sure the paths are correct, or the monitor will be messed up. Easiest way to do this is to copy and paste the `baleTrakPro` from the asset textures folder, into your project, and reroute the textures, or you can edit the text version of the i3d if you know how to do it. 
### Step 4: Basenode and Index Path
Make note of the monitor nodes (index path) for future reference. Should look something like "0>0|5|10|0|2|0|0|0|0" depending on where you put the monitor at. These can be found on the "Attributes" window in GIANTS Editor. ![Screenshot of GIANTS Editor](https://github.com/Lazy-E-Modding/MonitorAddons/blob/a880b6b8155dd339d21798ea18c3de59da6320f1/Screenshot%202023-10-01%20111826.jpg) Make sure to make note of the root node as it will be used in the next steps to make this easier.
**The XML template will be set up for you to replace `BASENODE` with the node that you have noted from above to allow for easy copy and paste**
### Step 5: Opening the Template XML
Open the XML template up in a text editor of your choosing. You'll notice it is a simplified tractor XML, and only has the code that you need to do this, along with some design config layouts.
### Step 6: i3d Mappings
 Identify the `<i3dMappings>` at the bottom of the xml from Step 5. If the xml that you are adding the bale monitor to already has `i3dMappings`, then just copy the nodes over that are in the child area. Those should look something like: 
```xml
 <i3dMapping id="MonitorMountNode" node="0>" /> <!-- Base Node -->
  <i3dMapping id="BaleTrakBaleMonitor" node="BASENODE|0" />
  <i3dMapping id="Clamps" node="BASENODE|0|0" />
  <i3dMapping id="ClampBraket" node="BASENODE|0|0|0" />
  <i3dMapping id="Pivot1" node="BASENODE|0|0|0|0" />
  <i3dMapping id="Mount" node="BASENODE|0|0|0|0|0" />
  <i3dMapping id="Monitor" node="BASENODE|0|0|0|0|0|0" />
  <i3dMapping id="Display" node="BASENODE|0|0|0|0|0|0|0" />
  <i3dMapping id="FillLevelBars" node="BASENODE|0|0|0|0|0|0|1" />
  <i3dMapping id="GlowBackground" node="BASENODE|0|0|0|0|0|0|2" />
  <i3dMapping id="baleCountNode" node="BASENODE|0|0|0|0|0|0|3" />
  <i3dMapping id="baleSizeNode" node="BASENODE|0|0|0|0|0|0|4" />
  <i3dMapping id="baleFieldCountNode" node="BASENODE|0|0|0|0|0|0|5" />
  <i3dMapping id="Cylinder" node="BASENODE|0|0|0|0|0|0|6" />
```

If you xml that you are adding to **DOES NOT** have the `<i3dMappings>` in it, copy the whole parent and child, should look something like this: 
```xml
<i3dMappings>
  <i3dMapping id="MonitorMountNode" node="0>" /> <!-- Base Node -->
  <i3dMapping id="BaleTrakBaleMonitor" node="BASENODE|0" />
  <i3dMapping id="Clamps" node="BASENODE|0|0" />
  <i3dMapping id="ClampBraket" node="BASENODE|0|0|0" />
  <i3dMapping id="Pivot1" node="BASENODE|0|0|0|0" />
  <i3dMapping id="Mount" node="BASENODE|0|0|0|0|0" />
  <i3dMapping id="Monitor" node="BASENODE|0|0|0|0|0|0" />
  <i3dMapping id="Display" node="BASENODE|0|0|0|0|0|0|0" />
  <i3dMapping id="FillLevelBars" node="BASENODE|0|0|0|0|0|0|1" />
  <i3dMapping id="GlowBackground" node="BASENODE|0|0|0|0|0|0|2" />
  <i3dMapping id="baleCountNode" node="BASENODE|0|0|0|0|0|0|3" />
  <i3dMapping id="baleSizeNode" node="BASENODE|0|0|0|0|0|0|4" />
  <i3dMapping id="baleFieldCountNode" node="BASENODE|0|0|0|0|0|0|5" />
  <i3dMapping id="Cylinder" node="BASENODE|0|0|0|0|0|0|6" />
</i3dMappings>
```
_**If you do not do this right, the rest of this installation tutorial will be a pain. I will not provide any more support than what is here. It is simple. If you can not do this, then please just don't do the edit.**_

For any spot that you see `BASENODE` in the i3dMappings, you need to replace it with the base node that you obtained from Step 4

### Step 7: Lights
In the xml that you are editing, locate the `<lights>` portion. You'll add line 45 in the template xml to your `<defaultLights>` portion of your XML. An example of the line to add to the default lights area is here:
```xml
<defaultLight shaderNode="GlowBackground" lightTypes="0" intensity="1.5"/>
```

### Step 8: Animations
Copy the animation from the template xml to your xml in the animations area, this will allow the animations of the monitor to work. 
```xml
<animation name="BALERFILLLEVEL">
            <part node="FillLevelBars" startTime="0.0" endTime="1.0" shaderParameter="visibilityCutThreshold" shaderStartValues="1 0 0 0" shaderEndValues="0 0 0 0" />
        </animation>
```
_Note: If you have multiple monitor options, as in more than one position for a bale monitor, you'll need to create multiple animations._

### Step 9: Adding Dashboard Live to the XML Adding the Dashboard Live Lines

Locate the `<dashboard>` area in the xml that you are editing. Once that is done, add lines 75-78 from the template XML to your XML, inside of the `<groups>` child. 
```xml
<groups>
            <group name="MOTOR_STARTING" isMotorStarting="true"/>
            <group name="MOTOR_ACTIVE" isMotorStarting="true" isMotorRunning="true"/>
            <group name="BACK_ATTACHMENT" attacherJointIndices="1 2 3"/>
            <group name="DBL_BALER" dbl="base_hasSpec" dblOption="spec_baler" attacherJointIndices="1 2 3" />
            <group name="PAGE1" dbl="page" page="1"/>
            <group name="PAGE2" dbl="page" page="2"/>
            <group name="PAGE3" dbl="page" page="3"/>
</groups>
```
Adding this will allow you to switch between screens, and allow the displays to be blank if criteria are not met. 

Next, you'll need to add the following, or the xml lines 82 - 87 from the template xml to your xml. Make sure that these are in `<dashboardLive>` or it will not work. 
```xml
<dashboardLive>
        <dashboard valueType="baler" 	cmd="balecounttotal"	 		joints="1 2 3 "			displayType="TEXT" 			node="baleCountNode" 		groups="DBL_BALER MOTOR_ACTIVE PAGE1"		trailer="1"			textColor="0 0 0 1"		textSize="0.008"	textMask="000"	font="DIGIT"	textAlignment="RIGHT"/>
        <dashboard valueType="baler" 	cmd="balecountanz"	 		joints="1 2 3 "			displayType="TEXT" 			node="baleFieldCountNode" 		groups="DBL_BALER MOTOR_ACTIVE PAGE2"		trailer="1"			textColor="0 0 0 1"		textSize="0.008"	textMask="000"	font="DIGIT"	textAlignment="RIGHT"/>
        <dashboard valueType="base"		cmd="fillLevel"		option="percent"	partition="1"		joints="1 2 3"		displayType="ANIMATION" 	animName="BALERFILLLEVEL"		groups="MOTOR_ACTIVE DBL_BALER"	trailer="1"		minValueAnim="1"	maxValueAnim="100"	/>
        <dashboard valueType="baler" 	cmd="baleSize"	option="current"	joints="1 2 3 "			displayType="TEXT" 			node="baleSizeNode" 		groups="MOTOR_ACTIVE DBL_BALER PAGE3"	textColor="0 0 0 1"		textSize="0.008"	textMask="000 CM"	font="DIGIT"	textAlignment="RIGHT"/>
</dashboardLive>
```
  
### Wrapping Up
As long as you followed the instructions, and set up the base node right, replaced it in the i3d mappings, and added all the lines to the XML correctly, there should not be any issues. **I (Lazy E Modding) will not take any responsibility for mods not working, and will not fix, or provide one on one support. This is a simple edit, and the tutorial walks you through step by step. ** I have more plans for the future, but if I have to help each person that wants a bale monitor, those ideas will remain private. 

## Credits

I do ask that if you use this mod, or code, you add Lazy E Modding as a contributor to your mod. Don't be the person that doesn't do it, and ruins everything for everyone else. 

You should reference Lazy E Modding in the author tab, and in any website, modDesc, or post, there should be a reference to Lazy E Modding for the bale monitor. All social posts should tag Lazy E Modding on the respective platforms. Giving credit is something that is easy, and should be done out of a sign of respect and thanks for the addition. 
