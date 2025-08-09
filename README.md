# Cobot.Detect
Cobot.Detect project, aiming to provide comprehensive monitoring for collaborative robot (cobot) work areas through an on-device privacy-centric visual AI solution.

<!--
![Cobot.Detect workflow](assets/cobot.detect_workflow.jpg) -->

<img src="assets/cobot.detect_workflow.jpg" alt="Cobot.Detect workflow" width="600"/>

### Workflow Steps

1. **Continual Training**  
   Utilize both the COCO-Seg and Cobot datasets to perform continual training of the model.

2. **Model Optimization**  
   Optimize the trained model using [Qualcomm AI Hub](https://aihub.qualcomm.com/).

3. **Device Deployment**  
   Deploy the optimized model to devices running Windows and powered by Snapdragon processors.

4. **On-Device Data Privacy**  
   By keeping data on-device, Cobot.Detect seamlessly integrates with cobot applications, safeguarding trade secrets and the privacy of people captured in the monitored environment..

   

* * *
# 🗂️ End-to-End Cobot Dataset Generation Workflow

* * *

# 🔬 Model Compilation Test on Snapdragon X Elite

Table 1 shows the results of compiling “yolo-v[11,8]n.pt” with different target models for the Snapdragon X Elite CRD.


| Model/Format           | YOLOv11n-seg | YOLOv8n-seg |            Runtime                   |              link            |
|------------------------|:------------:|:------------:|:-------------------------------:|:---------------------------|
| **onnx**               | ✅ 31.7ms 133MB CPU304| ✅7.1ms 17MB NU337|   	ONNX Runtime | |
| **tflite**             | ❌            | ❌                        |                                                           |
| **qnn_context_binary** | ❌            | ✅5.5ms 5MB NPU336                       | QNN API | [details](https://app.aihub.qualcomm.com/jobs/jpew8mj1p/) |
| **precompiled_qnn_onnx** | ❌          | ✅5.4ms 17MB NPU331                       | ONNX Runtime | [details](https://app.aihub.qualcomm.com/jobs/jpvrek1z5/) |
| **qnn_dlc**            | ✅ 5.4ms 5MB NPU415            | ✅5.0ms 20MB NPU326                 |  QNN API | [details](https://app.aihub.qualcomm.com/jobs/jg9yknvl5/) |

`QNN API/Backend/SDK needs to run within Ubuntu 20.04`  [• You have an Ubuntu 20.04 or WSL2 on Windows with an Ubuntu 20.04 development environment.](https://www.qualcomm.com/developer/software/neural-processing-sdk-for-ai)

Based on the data in this table and the environmental constraints of the QNN API, choosing YOLOv8 together with precompiled_qnn_onnx may be the optimal solution.
