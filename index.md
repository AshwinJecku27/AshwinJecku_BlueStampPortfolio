# Optical Character Reader with Raspberry Pi
In this project, a camera sends its input to the Raspberry Pi system. From there, the image is analyzed and we get some data back. With this data, the computer can "read" the text in the camera input

You should comment out all portions of your portfolio that you have not completed yet, as well as any instructions:
```HTML 
<!--- This is an HTML comment in Markdown -->
<!--- Anything between these symbols will not render on the published site -->
```

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Ashwin J | Liberty High School | Computer Science | Incoming Freshmen

**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



# Second Milestone


<iframe width="560" height="315" src="https://www.youtube.com/embed/7Ovl1BxyDWE?si=jw2OouAmnSlHZ0PO" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

For your second milestone, explain what you've worked on since your previous milestone. You can highlight:
- Technical details of what you've accomplished and how they contribute to the final goal: I have connected the ArduCam to the Raspberry Pi.
- What has been surprising about the project so far: Something that really suprised me was that the camera was really easy to connect and worked the first time.
- Previous challenges you faced that you overcame: I had to find the perfect distance to be able to view the image with good accuracy.
- What needs to be completed before your final milestone: I need to add the better camera in along with importing Open AI to be able to run the output through Chat GPT.

# First Milestone


<iframe width="560" height="315" src="https://www.youtube.com/embed/DmBi6qRRpzo?si=_fbl6ZUHSODxkclB" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

For your first milestone, describe what your project is and how you plan to build it. You can include:
- An explanation about the different components of your project and how they will all integrate together: The components in this milestone include the Raspberry Pi 4 along with the code. The code run through the Raspberry Pi, allowing it to break down uploaded images to be able to isolate the text in the image.
- Technical progress you've made so far: So far, I have set up the Raspberry Pi 4 along with the Micro SD Card. Additionally, I have connected the ArduCam to the Raspberry Pi.
- Challenges you're facing and solving in your future milestones: A challenge I have faced is having to set up a virtual environment to be able to code the Raspberry Pi. An upcoming challenge in the way of getting to my second Milestone is coding the input from the ArduCam.
- What your plan is to complete your project: My plan to complete the project is to: Receive camera input, run it through the code to break down the input, and finally, be able to have a program that reads the text in the camera input.

# Schematics 
Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad because it can be done easily and for free in the browser. 

# Code
Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. 

```c++
void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  Serial.println("Hello World!");
}

void loop() {
  // put your main code here, to run repeatedly:

}
```

# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Raspberry Pi 4 | The code is downloaded on this and it manages the different aspects of the OCR. | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| ArduCam IMX08 | The autofocus feature of this camera is used to detect the letters specifically | $Price | <a href="[https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://www.amazon.com/Arducam-Raspberry-Camera-Autofocus-Acrylic/dp/B0BX7VFT8Q/ref=asc_df_B0BX7VFT8Q/?tag=hyprod-20&linkCode=df0&hvadid=692875362841&hvpos=&hvnetw=g&hvrand=14284207478659014140&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9033294&hvtargid=pla-2281435177418&psc=1&mcid=6dfe77b57b5934baa002d4b66313cd08&hvocijid=14284207478659014140-B0BX7VFT8Q-&hvexpln=73&gad_source=1)"> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.
