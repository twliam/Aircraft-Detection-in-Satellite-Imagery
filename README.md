## Aircraft-Detection-in-Satellite-Imagery
GA Capstone Project

### The Challenge
Traffic tends to be more dynamic at Seletar Airport due to its primary use as an aerodrome for general aviation (GA) and business flights, both of which tend to be non-scheduled in nature. The only scheduled flights are by Malaysian operator Firefly. To further exacerbate the issue, traffic volume has also been increasing post-covid. It is tough to know when to expect more air traffic movement except through shared observations among the local general aviation community, which isn't particularly large. This uncertainty is particularly costly due to the high price tag of GA flying in Singapore.‍

## Problem Statement
GA pilots (both private license holders and students) thus need a way to monitor activity trends at Seletar Airport so as to better plan their flights to be more cost effective. 

## Possible Solutions
After communicating with some club members, most agreed it would be nice to see some numbers with regards to popular usage timings at the airport. Two potential solutions came to mind:
1. Analyze flight data extracted from a publicly available flight tracker such as flightradar24
2. Implement a means to automate the community observations mentioned in the previous sction.  

‍While combining the two solutions would be the most ideal, we focus first on automating the observation of airport activity. Firstly because it is somewhat of a familiar option, and secondly because publicly available flight trackers do not have information on all GA flights [footnote about the data they use]. This project will serve as a proof of concept to show that it is possible to adapt an object detection model that has been fine-tuned for the more general task of detecting civil aircraft, as a potential means to automate the observation of traffic over an aerodrome.  

This could be possible with the advancement in revisit capabilities of available satellite constellations e.g. Planet's SkySat Constellation being capable of rapid revisits of up to 12 times per day. Although the way low-orbit satellites work does not allow for constant monitoring, it should be sufficient for tracking trends over a period of time.  

## The Project
In this first iteration, the aim is to train an object detection model to accurately identify and locate aircraft within satellite images, achieving at least 0.75 mAP.

### Data
The Airbus Aircraft Dataset contains 103 satellite images with corresponding annotations for each target airplane. These are sample images from the Airbus OneAtlas platform.

### Models
2 Models (YOLOv7 and YOLOv8) are fine-tuned on the Airbus Aircraft Dataset for use in the satellite imagery detection task.

### Target Metric
Mean Average Precision (mAP)  
The mAP incorporates the trade-off between precision and recall and considers both false positives (FP) and false negatives (FN). An aircraft detection system would need to balance recall with precision to ensure that capacity is correctly monitored. The presence of too many false detections (whether positive or negative) would be highly detrimental to efficiency and the effectiveness of the model.

## Limitations & Drawbacks
**1. Cost of satellite tasking and imagery vs cost of simply flying.**  
Satellite tasking isn't the cheapest of solutions, although this is mitigated by time potentially spent stuck on the ground (Upwards of $550/hr for training flights) and having to be at the airport. The consideration here would be human effort vs cost of automation.  

**2. Weather**  
Weather over the airfield would block satellite imaging, although this could also be an opportunity to visually capture cloud cover and other weather trends which are important considerations for flying under visual flight rules (VFR).

**3. Quantity and Quality of Training Data**  
More images with a greater variety of airfields, backgrounds and aircraft types would definitely aid in increasing the model's ability to detect aircraft in novel environments, such as over large water bodies or flying in forested training areas.

## Future Directions
As it stands, more features, such as a dashboard for easy monitoring, needs to be built on top of this model before it can be put into production for its desired use case but the model itself can be used in several other situations as well. An extension to this project in the pipeline would be to recognize, differentiate and detect military aircraft in addition to civil ones for ntelligence applications. This would also extend its suitability in being adapted for an aerodrome like Changi where there is military traffic too. While ground-based monitoring capabilities (such as radar, MLAT, ADS-B) are robust, brings a fresh perspective and is intuitively easier to make sense of. Being able to visually pick out potential hot spots or high traffic clusters may help in informing aircraft maneuvering area processes and utilization for greater safety and efficiency.

On that note, an aircraft parking facility such as Asia Pacific Aircraft Storage in Alice Springs, Australia, could employ a similar satellite-based solution for monitoring capacity. At time of writing, these further developments would still require careful consultation with data providers to determine the feasibility of such a project subject to the exact capabilities of currently available satellite constellations. To end off, here is a sample video on SkySat's video capability SkySat Video of Dubai, United Arab Emirates - YouTube.

Credits:  
The Airbus Aircraft Detection Dataset a is licensed under the Creative Commons BY-NC-SA 4.0 International license:
https://creativecommons.org/licenses/by-nc-sa/4.0/ and was obtained from https://www.kaggle.com/datasets/airbusgeo/airbus-aircrafts-sample-dataset
