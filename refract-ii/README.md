![](../images/line3.png)

### Refraction and Fresnel II

<sub>[previous](../refract/README.md#user-content-refraction-and-fresnel) • [home](../README.md#user-content-ue5-intro-to-materials) • [next](../animation/README.md#user-content-animation)</sub>

![](../images/line3.png)

Now lets really move it up a notch and add a normal map to give the glass some texture.

<br>

---


##### `Step 1.`\|`UE5MAT`|:small_blue_diamond:

Press <kbd>Play</kbd> and look at how the refraction increases around the edges.

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/787afa75-a939-44bd-a7d3-837a62523a8a

![](../images/line2.png)

##### `Step 2.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: 

Add a **Text** actor and change the color and size and set it to **Text** `MI_Glass`.  Place it and rotate it on top of the material ball.

![place text on toop of material ball](images/miBasicTextTitle.png)

![](../images/line2.png)

##### `Step 3.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Lets adjust the strength of the fresnel by turning the **Exponent In** to a variable. Open up **M_Glass** and add another **Scalar Parameter** and set the default to `5`.  Call it `FresnelExponent` and attach it to the **ExponentIn** pin. Set the **Default Value** to `5.0`, set the **Group** to `Glass Properties` and the **Set Priority** to `17`.

![add scalar paramter called fresnel exponent](images/addFrenelExpScalarParam.png)

![](../images/line2.png)

##### `Step 4.`\|`UE5MAT`|:small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Right click on* **MI_Glass** and select **Duplicate**.  Call the new material **MI_GlassFrosted**.  We will add a frosted glass effect.

![assign T_FrostedGlass](images/MIFrostedGlass.png)

![](../images/line2.png)

##### `Step 5.`\|`UE5MAT`| :small_orange_diamond:

Download [T_FrostedGlass.tga](../Assets/T_FrostedGlass.TGA) normal map and import into the game. 

![assign T_FrostedGlass](images/copyNormal.png)

![](../images/line2.png)

##### `Step 6.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond:

Duplicate the glass ball and title text.  Move it to the middle of the room.  Change the title to `MI_FrostedGlass` and assign the **MI_FrostedGlass** material to the duplicated ball.

![assign T_FrostedGlass](images/dupeFrosted.png)

![](../images/line2.png)

##### `Step 7.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

Assing the **Normal** texture to be `T_FrostedGlass`. Change the **Alpha** scalar to `0.4`.

![assign T_FrostedGlass](images/assignTFrostedGlass.png)

![](../images/line2.png)

##### `Step 8.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

We can change the strength of the falloff of the fresnel node by adjusting the **Exponent**.

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/2f2d2a13-02de-4a66-abbd-3b030a655b57


![](../images/line2.png)

##### `Step 9.`\|`UE5MAT`| :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

*Press* the <kbd>Play</kbd> button and go up to both glass material balls.  The textured one really stands out and the refraction is now even more exagerated.

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/a46a4ec8-6618-4bc3-8373-bde042af0d20

![](../images/line2.png)

##### `Step 10.`\|`UE5MAT`| :large_blue_diamond:

To add a glow to the edge we will open up **M_Glass** and add a new **Static Switch Parameter** and call it `EdgeGlow?`.  Set the **Group** to `GlassProperties` and **Sort Priority** to `17`.

![add edge glow scalar](images/GLowStaticParam.png)

![](../images/line2.png)

##### `Step 11.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: 

 Add a **Constant Scalar** set to `0` to the **False** pin.  Add another **Scalar Paremeter** called `EdgeGlow`. Set the **Group** to `GlassProperties` and **Sort Priority** to `18`. 

 Add a **Fresnesl** node and a multiply node.  Put the output of the **Fresnel** to the **B** side of the multiply node.

![add edge glow switch](images/glowLogic.png)

![](../images/line2.png)


##### `Step 12.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: 

Send the output of **EdgeGlow** to the **A** side of the multiply node.  Send the output of the multiply node to the **EdgeGlow | True** pin.  Send the **Edge Glow** output pin to the **Emissive Color** pin.

Add comments with `Edge Glow` around the emissive pins and `Refraction` around the refraction pins.

![multiply glow fresnel](images/sendToEmissive.png)

![](../images/line2.png)

##### `Step 13.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Go to **Materials | Material Instances** and right click `MI_GlasFrosted` and select **Duplicate**.  Call this new material instance `MI_GlassFrostedGlow`.

![multiply glow fresnel](images/dupefrostglssglow.png)

![](../images/line2.png)

##### `Step 14.`\|`UE5MAT`| :large_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:  :small_blue_diamond: 

Go back to the editor and duplicate the material ball and title and put it in front of the third pillar.  Drag **MI_GlassFrostedGlow** to this duplicate ball. Change the title to `MI_GlassFrostedGlow`.

![multiply glow fresnel](images/dupeGlowMat.png)

![](../images/line2.png)

##### `Step 15.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: 

*Press* the <kbd>Play</kbd> button and now look at all three material balls.  We have made progressive improvements and our third ball is terrific! Play around with the amount of glow to your liking.

https://github.com/LSU-UE5/UE5-Materials/assets/5504953/990c21ef-fbe0-42b0-84bf-e6f33d2083c3

![](../images/line2.png)

##### `Step 16.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond:   :small_blue_diamond: 

Go to **Materials | Material Functions** and right click and create a new **Material | Material Function** and call it `MF_Glass`.  Now go to **M_Glass** and *copy and cut* all the nodes in both comment boxes.

![organize outliner](images/newMatFunc.png)

![](../images/line2.png)

##### `Step 17.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond:

*Paste* all the nodes into the new **MF_Glass** function.  Change the name of the output node and call it `Emissive`.  Hook it up to the **Edge Glow** output pin.

Add another **Function Output** and connect it to the **Lerp** node.  Change the **Sort Priority** to `1`.

![organize outliner](images/glassFuncComplete.png)

![](../images/line2.png)

##### `Step 18.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go back to **M_Glass** and drag in **MF_Glass** and connect it to the **Emissive Color** and **Refraction** pins.  Press the <kbd>Apply</kbd> button.  Now we are done.

![organize outliner](images/addMFGlass.png)

![](../images/line2.png)

##### `Step 19.`\|`UE5MAT`| :large_blue_diamond: :small_orange_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond: :small_blue_diamond:

Go to the **Outliner** and make sure eveything is in **Room 7**.  Rename items so they make sense.

![organize outliner](images/organizeOutliner.png)

![](../images/line2.png)

##### `Step 20.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond:

Select the **File | Save All** then press the <kbd>Revision Control</kbd> button and select **Submit Content**.  If you are prompted, select **Check Out** for all items that are not checked out of source control. Update the **Changelist Description** message and with the latest changes. Make sure all the files are correct and press the <kbd>Submit</kbd> button. A confirmation will pop up on the bottom right with a message about a changelist was submitted with a commit number.

![save all and submit to perforce](images/submitP4.png)

![](../images/line2.png)

##### `Step 21.`\|`UE5MAT`| :large_blue_diamond: :large_blue_diamond: :small_blue_diamond:

Sometimes not all files get submitted to Unreal especially for files that don't show up in the editor.  It is good practice one you submit in **Unreal** and quit the game to right click on the top most project folder and select **Reconcile Offline Work...**.

This will either give a message saying ther is nothing to reconcile or bring up a tab.  Make sure that these are **NOT** files in the **Intermediate** and **Saved** folders as these should be ignored from the `.p4ignore`.

If the files are in **Content** or **Configuration** then press the <kbd>Reconcile</kbd> button.  Then submit the changes with a message and press the <kbd>Submit</kbd> button.

![reconcile offline work](images/reconcile.png)

![](../images/line.png)

<!-- <img src="https://via.placeholder.com/1000x100/45D7CA/000000/?text=Next Up - Animation"> -->
![next up next tile](images/banner.png)

![](../images/line.png)

| [previous](../refract/README.md#user-content-refraction-and-fresnel)| [home](../README.md#user-content-ue5-intro-to-materials) | 

[next](../animation/README.md#user-content-animation)|
|---|---|---|
