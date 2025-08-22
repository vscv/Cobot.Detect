<div align="center">
<img src="assets/CD-logo-s-w.jpeg" alt="CD-logo" width="300"/>
</div>

---

# Cobot.Detect
Cobot.Detect project, aiming to provide comprehensive monitoring for collaborative robot (cobot) work areas through an on-device privacy-centric visual AI solution.




## 🏗️ Workflow

<!--
![Cobot.Detect workflow](assets/cobot.detect_workflow.jpg) -->
<div align="center">
<img src="assets/cobot.detect_workflow.jpg" alt="Cobot.Detect workflow" width="600"/>
</div>

1. **Continual Training**  
   Utilize both the COCO-Seg and Cobot datasets to perform continual training of the model.

2. **Model Optimization**  
   Optimize the trained model using [Qualcomm AI Hub](https://aihub.qualcomm.com/).

3. **Device Deployment**  
   Deploy the optimized model to devices running Windows and powered by Snapdragon processors.

4. **On-Device Data Privacy**  
   By keeping data on-device, Cobot.Detect seamlessly integrates with cobot applications, safeguarding trade secrets and the privacy of people captured in the monitored environment..

   

* * *
# 🗂️ Cobot Dataset Generation

<div align="center">
  <a href="https://github.com/vscv/NaiveSAM/tree/main/files/End2End_demo">
    <img src="https://img.shields.io/badge/GitHub-NaiveSAM-blue?logo=github&style=for-the-badge" alt="NaiveSAM Demo Link">
  </a>
</div>

- **Auto Annotation Overview**
  
  [Annotation UI](https://github.com/user-attachments/assets/1345436b-0d57-4b72-9e9d-fe161b5efe08)

> 🚀 **Full End-to-End Dataset Generation and Model Training Demo**  
> This section references the [`End2End_demo`](https://github.com/vscv/NaiveSAM/tree/main/files/End2End_demo) from our in-house auto-annotation tool
[@vscv/NaiveSAM](https://github.com/vscv/NaiveSAM) repository.  
> Check out the IPython notebook directly!

<!--
### ✨ About This Section

- All steps, sample codes, and workflow diagrams in this section are from [NaiveSAM/End2End_demo](https://github.com/vscv/NaiveSAM/tree/main/files/End2End_demo).
- For more technical details, code, and extended applications, please refer to the original project.

---

> 💡 **TIP:**  
> To quickly copy, run, or customize this workflow, please check the `End2End_demo` directory in the [NaiveSAM repository](https://github.com/vscv/NaiveSAM).
-->


* * *

# 🔬 Model Compilation Test on Snapdragon X Elite

Table 1 shows the results of compiling “yolo-v[11,8]n.pt” with different target models for the Snapdragon X Elite CRD.


| Model/Format           | YOLOv11n-seg | YOLOv8n-seg |            Runtime                   |              link            |
|------------------------|:------------:|:------------:|:-------------------------------:|:---------------------------|
| **onnx**               | ✅ 31.7ms 133MB CPU304| ✅7.1ms 17MB NU337|   	ONNX Runtime | |
| **tflite**             | ❌<sup>[1]</sup>| ❌<sup>[1]</sup>       |                                                           |
| **qnn_context_binary** | ❌<sup>[2]</sup>            | ✅5.5ms 5MB NPU336                       | QNN API | [details](https://app.aihub.qualcomm.com/jobs/jpew8mj1p/) |
| **precompiled_qnn_onnx** | ❌<sup>[2]</sup>         | ✅5.4ms 17MB NPU331                       | ONNX Runtime | [details](https://app.aihub.qualcomm.com/jobs/jpvrek1z5/) |
| **qnn_dlc**            | ✅ 5.4ms 5MB NPU415            | ✅5.0ms 20MB NPU326                 |  QNN API | [details](https://app.aihub.qualcomm.com/jobs/jg9yknvl5/) |

`QNN API/Backend/SDK needs to run within Ubuntu 20.04`  [• You have an Ubuntu 20.04 or WSL2 on Windows with an Ubuntu 20.04 development environment.](https://www.qualcomm.com/developer/software/neural-processing-sdk-for-ai)

<!-- not goood and less clear...
Based on the data in this table and the environmental constraints of the QNN API, choosing YOLOv8 together with precompiled_qnn_onnx may be the conservative but easy-to-implement choice. However, we will insist on using the newer v11 model for further challenges.
-->
For performance evaluation and specification selection, we conducted real-device tests across different configurations using the Qualcomm AI HUB. Based on the data in this table and the environmental constraints of the QNN API, choosing YOLOv8 together with precompiled_qnn_onnx may be the conservative but easy-to-implement choice. However, we will continue to challenge ourselves by insisting on using the newer v11 model to explore its potential benefits further.

###### <sup>[1]</sup> ❌ FAILED   TargetRuntime.TFLITE is not a supported target for Snapdragon X Elite CRD.</small>
###### <sup>[2]</sup> ❌ FAILED   Model compile failed due to an internal error.


---
# 📦 BYOM

### Upload CP model

### Compile

<div align="left">
<img src="assets/Compile Job Results.jpg" width="400"/>
</div>


### Profile

<div align="left">
<img src="assets/Profile Job Results.jpg" width="400"/>
</div>


### Inference
<div align="left">
<img src="assets/Inference Job Results.jpg" width="400"/>
</div>


### Export the QNN model
QNN model format: Deep Learning Containers (DLCs)

<div align="left">
<img src="assets/Export the QNN model.jpg" width="400"/>
</div>


---
# QAIRT SDK

download site: https://qpm.qualcomm.com/#/main/tools/details/Qualcomm_AI_Runtime_Community

qairt version: 2.37.1.250807

Install doc: go to qairt/2.37.1.250807/docs/QNN/general/setup.html

<div align="left">
<img src="[assets/Profile Job Results.jpg](https://github.com/user-attachments/assets/47e755e4-a604-4d90-832d-70089b94d7d0)" width="400"/>
</div>

Then follow the `Windows Setup` to get the QAIRT in your Windows host.





We are trying to find out ...

---
# 💻 Practical Case: Cobot.Detect On Device

`Based on our retrained YOLOv11n-Segmentation model`


- **Case_1:**



https://github.com/user-attachments/assets/e6b0f4fe-40a4-4719-87c8-3f08acd50ae9

https://github.com/user-attachments/assets/239e5bd0-9be6-449a-88af-651d54c5e252

https://github.com/user-attachments/assets/d325b611-2307-4402-94c2-ec0111afdd8f


- **Case_2:**

<!--
https://github.com/user-attachments/assets/093d322c-b0cf-41b6-aa62-c2c091a60d75
loop autoplay muted
-->
<div align="center">
  <video src="https://github.com/user-attachments/assets/093d322c-b0cf-41b6-aa62-c2c091a60d75" controls width="400" >
    <!-- 如果瀏覽器不支援，則顯示此文字 -->
    Your browser does not support the video tag.
  </video>
</div>


person_mosaic on-device
<!--
<div align="center">
<img src="assets/FoxconnBuildsRoboticsforHealthcare_ycut.mp4_00015_mask_red.jpeg" alt="Cobot.Detect workflow" width="400"/>
</div>

<div align="center">
<img src="assets/FoxconnBuildsRoboticsforHealthcare_ycut.mp4_00039_mask_red.jpeg" alt="Cobot.Detect workflow" width="400"/>
</div>


<div align="center">
<img src="assets/FoxconnBuildsRoboticsforHealthcare_ycut.mp4_00015_mosic.jpeg" alt="Cobot.Detect workflow" width="400"/>
</div>

<div align="center">
<img src="assets/FoxconnBuildsRoboticsforHealthcare_ycut.mp4_00039_mosaic.jpeg" alt="Cobot.Detect workflow" width="400"/>
</div>
-->

<table>
  <tr>
    <td><div align="center"><img src="assets/FoxconnBuildsRoboticsforHealthcare_ycut.mp4_00015_mask_red.jpeg" alt="Cobot.Detect workflow" width="400"/></div></td>
    <td><div align="center"><img src="assets/FoxconnBuildsRoboticsforHealthcare_ycut.mp4_00039_mask_red.jpeg" alt="Cobot.Detect workflow" width="400"/></div></td>
  </tr>
</table>

<table>
  <tr>
    <td><div align="center"><img src="assets/FoxconnBuildsRoboticsforHealthcare_ycut.mp4_00015_mosic.jpeg" alt="Cobot.Detect workflow" width="400"/></div></td>
    <td><div align="center"><img src="assets/FoxconnBuildsRoboticsforHealthcare_ycut.mp4_00039_mosaic.jpeg" alt="Cobot.Detect workflow" width="400"/></div></td>
  </tr>
</table>

<table>
  <tr>
    <td><div align="center"><img src="assets/FoxconnBuildsRoboticsforHealthcare_ycut.mp4_00015_mask-box-label.jpeg" alt="Cobot.Detect workflow" width="400"/></div></td>
    <td><div align="center"><img src="assets/FoxconnBuildsRoboticsforHealthcare_ycut.mp4_00039_mask-box-label.jpeg" alt="Cobot.Detect workflow" width="400"/></div></td>
  </tr>
</table>

<table>
  <tr>
    <td><div align="center"><img src="assets/FoxconnBuildsRoboticsforHealthcare_ycut.mp4_00015_mosaic-box-label.jpeg" alt="Cobot.Detect workflow" width="400"/></div></td>
    <td><div align="center"><img src="assets/FoxconnBuildsRoboticsforHealthcare_ycut.mp4_00039_mosaic-box-label.jpeg" alt="Cobot.Detect workflow" width="400"/></div></td>
  </tr>
</table>



- **Case_3:**
  Using VLM for `visual question answering`

<div align="center">
<img src="assets/cobot_VQA_001.jpg" width="400"/>
</div>

<div align="center">
<img src="assets/cobot_VQA_002.jpg" width="400"/>
</div>

<div align="center">
<img src="assets/cobot_VQA_003.jpg" width="400"/>
</div>

<div align="center">
<img src="assets/cobot_VQA_004.jpg" width="400"/>
</div>

 
- **Case_4:**
- **Case_5:**



### Windows AI PC?notebook?




### video streams
### show result on video wall

---
