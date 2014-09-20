AUTOPILOT
How the Navio project came about

AUTOPILOT FOR RASPBERRY PI
The Navio autopilot shield

There is no need to explain all of the features of the Raspberry Pi and how it is making embedded development easier. When working with the Raspberry Pi platform, we did however find that autopilot applications are some what limited and thus we established the Navio project to overcome this.

Prior to using the Raspberry Pi, a lot of time was invested in building a commercial UAV autopilot based on the STM32 microcontroller, the same microcontroller that is used in most autopilots. When development of the core software was completed our focus became integration of new payloads, i.e. a new means of communication and new sensors. We found this process very complicated, having to write drivers for each new piece of electronics, even though we knew that they already existed. Development and debugging tools were bulky and kept us tied to the workplace. It was from these issues that the idea of a Linux autopilot first crossed our minds.

At first Navio started as a hobby project at weekends. With progression of the project and increasing group confidence we decided to quit our jobs to work on the Linux autopilot full time.

We started investigating the options available to create an open and powerful Linux autopilot platform, deducing the Raspberry Pi as the obvious choice. We received great support from the community, finding a lot of readily available code and tutorials combining all of the power and flexibility of Linux. When we first sent data over a 3G network we just couldn't believe how easy it was, compared to our previous setup. It was just like on a desktop PC. Simply install the drivers and you are ready to go!

Autopilot is much more than just a processor running an OS. It needs a way to determine its state, its place on Earth, and be able to control actuators. It takes many sensors and servos to fly a plane or multicopter. We needed a 9DOF inertial measurement unit for orientation, GPS for position, barometric pressure sensor for altitude and multiple control outputs. We thus returned to the drawing board, well technically not to a drawing board, but to CAD software, and designed the Navio. In the process an ADC was added for voltage and current monitoring, an RGB LED to show statuses and connectors were made compatible with existing hardware.

Navio sits on top of the Raspberry Pi GPIO header and is fixed with a standoff and bolt. It met our specification of being very compact, making it possible to fit in tight spaces inside small drones, whilst packing everything needed for a full featured autopilot. For our own plane we have chosen to remove some of the sockets on Raspberry Pi to save weight and reduce size.

When we first presented the idea to the community, the feedback was great. A Raspberry Pi autopilot actually sounds sweet. It was quickly drawn to our attention that the autopilot has to be strict real-time, and it is not something you expect from Linux straight out of the box. We started experimenting. From the team's previous experience with low latency audio processing on Linux, we knew that it can work real-time if tuned the right way.

With a real-time kernel and proper task priority settings we have outperformed what we had on STM32. We are able to run inertial measurement unit code at 3000 times per second, including reading data from sensors, computing roll, pitch and yaw angles and outputting them through Wi- Fi to console. Even when running alongside computational heavy processes like compiling, the performance was stable. This assured us that there is no need to overcomplicate the setup with a secondary processor for sensor reading.

In our opinion, the Raspberry Pi with Navio is not a commercial autopilot product, but something that lets you evaluate your ideas and test new algorithms. The key factor was the ability to run multiple applications with autopilot in parallel. The other feature of Raspberry Pi is the ease of development; just open your favourite code editor, compile the file and run the application.

With hardware and OS complete we moved to the autopilot code itself. At first we trialled code to check if the sensors and peripherals were working as expected. When we got Navio to control servos it was time to try it on something real. We took an RC car off the shelf, installed Navio on top and added webcam and Wi-Fi. After several hours of coding we were able to control it from a laptop keyboard and to get live video streaming on screen! Immediately we took a tour around the house, feeling like secret service ROV operators. We revealed some corners that have not been vacuumed for years, and even found the place where second socks go.

We then identified that we needed software to actually fly a plane, but we did not want to reinvent the wheel. From our previous experience it was clear that there is no quick way to write an autopilot. It takes a lot of testing and working on the details to actually make a reliable system. We all know how many open source autopilots are out there, it was just a question of picking the right one.

We were following the ArduPilot project from the very beginning, and when we found out that the team is working on a Linux port, we decided that we should make it run on our platform. Mostly this requires small changes to the hardware specific parts, something we are actively working on. The test platform is already assembled, and we are sure that we are going to take flight soon!