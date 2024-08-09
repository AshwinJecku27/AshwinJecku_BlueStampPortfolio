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

![Headstone Image](logo.svg)
  
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/embed/F7M7imOVGug" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

- What you've accomplished since your previous milestone: I have added the AI API and the speaker which allows the AI's output to be heard through text to speech.
- What your biggest challenges and triumphs were at BSE: My biggest challenge was the IMX708 autofocus camera not working. The entire picture was blurry due to the autofocus not focusing.
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE



# Second Milestone


<iframe width="560" height="315" src="https://www.youtube.com/embed/7Ovl1BxyDWE?si=jw2OouAmnSlHZ0PO" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

- Technical details of what you've accomplished and how they contribute to the final goal: I have connected the ArduCam to the Raspberry Pi.
- What has been surprising about the project so far: Something that really suprised me was that the camera was really easy to connect and worked the first time.
- Previous challenges you faced that you overcame: I had to find the perfect distance to be able to view the image with good accuracy.
- What needs to be completed before your final milestone: I need to add the better camera in along with importing Open AI to be able to run the output through Chat GPT.

# First Milestone


<iframe width="560" height="315" src="https://www.youtube.com/embed/DmBi6qRRpzo?si=_fbl6ZUHSODxkclB" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

- An explanation about the different components of your project and how they will all integrate together: The components in this milestone include the Raspberry Pi 4 along with the code. The code run through the Raspberry Pi, allowing it to break down uploaded images to be able to isolate the text in the image.
- Technical progress you've made so far: So far, I have set up the Raspberry Pi 4 along with the Micro SD Card. Additionally, I have connected the ArduCam to the Raspberry Pi.
- Challenges you're facing and solving in your future milestones: A challenge I have faced is having to set up a virtual environment to be able to code the Raspberry Pi. An upcoming challenge in the way of getting to my second Milestone is coding the input from the ArduCam.
- What your plan is to complete your project: My plan to complete the project is to: Receive camera input, run it through the code to break down the input, and finally, be able to have a program that reads the text in the camera input.

# Code

```c++
import cv2
import pytesseract
from pytesseract import Output
from picamera2 import MappedArray, Picamera2, Preview
import openai
openai.api_key = ""

 #preprocessing functions; unused for now
def get_grayscale(image):
    return cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
 
 
def thresholding(image):
    return cv2.threshold(image, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)[1]
 
 
def opening(image):
    kernel = np.ones((5, 5), np.uint8)
    return cv2.morphologyEx(image, cv2.MORPH_OPEN, kernel)
 
 
def canny(image):
    return cv2.Canny(image, 100, 200)

#old cv2 code for legacy stack - leave commmented out
#cap = cv2.VideoCapture(0)
#cap.set(cv2.CAP_PROP_BUFFERSIZE, 1)

#picamera setup and configuration
picam2 = Picamera2()
picam2.configure(picam2.create_preview_configuration({"size": (1024, 768)}))
picam2.start_preview(Preview.QTGL)
picam2.start()
 
while True:
    # Capture frame-by-frame
    #ret, frame = cap.read()
    frame = picam2.capture_array()

    #preprocessing options- unused for now
    frame = get_grayscale(frame)
    #thresh = thresholding(gray)
    #opening = opening(gray)
    #canny = canny(gray)
    
    #character recognition
    d = pytesseract.image_to_data(frame, output_type=Output.DICT)
    n_boxes = len(d['text'])
    for i in range(n_boxes):
        if int(d['conf'][i]) > 60:
            (text, x, y, w, h) = (d['text'][i], d['left'][i], d['top'][i], d['width'][i], d['height'][i])
            # don't show empty text
            if text and text.strip() != "":
                prompt = "Provide some infromation about", text
                model = "text-davinci-003"
                response = openai.Completion.create(engine=model, prompt=prompt, max_tokens=10)
                generated_text = response.choices[0].text
                print(generated_text)
                frame = cv2.rectangle(frame, (x, y), (x + w, y + h), (0, 255, 0), 2)
                frame = cv2.putText(frame, text, (x, y - 10), cv2.FONT_HERSHEY_SIMPLEX, 1.0, (0, 0, 255), 3)
                cv2.imwrite("/home/ashwin/Downloads/OCR_Project"+str(i)+".png", frame) 
            # i += 1
 
    # Display the resulting frame
    cv2.imshow('frame', frame)
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break
 
# When everything done, release the capture
#cap.release()
cv2.destroyAllWindows()
```

# Bill of Materials

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Raspberry Pi 4 | The code is downloaded on this and it manages the different aspects of the OCR. | $72 | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| ArduCam IMX08 | The autofocus feature of this camera is used to detect the letters specifically | $59 | <a href="[https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/](https://www.amazon.com/Arducam-Raspberry-Camera-Autofocus-Acrylic/dp/B0BX7VFT8Q/ref=asc_df_B0BX7VFT8Q/?tag=hyprod-20&linkCode=df0&hvadid=692875362841&hvpos=&hvnetw=g&hvrand=14284207478659014140&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9033294&hvtargid=pla-2281435177418&psc=1&mcid=6dfe77b57b5934baa002d4b66313cd08&hvocijid=14284207478659014140-B0BX7VFT8Q-&hvexpln=73&gad_source=1)"> Link </a> |
