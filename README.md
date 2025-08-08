# Cobot.Detect
Cobot.Detect project, aiming to provide comprehensive monitoring for collaborative robot (cobot) work areas through an on-device privacy-centric visual AI solution.

* * *

# select model

| Model/Format           | YOLOv11n-seg | YOLOv8n-seg |            Note / Link                    |              link            |
|------------------------|:------------:|:------------:|:-------------------------------:|:---------------------------|
| **onnx**               | ✅ 31.7ms 133MB CPU304| ✅7.1ms 17MB NU337|   	ONNX Runtime | |
| **tflite**             | ❌            | ❌                        |                                                           |
| **qnn_context_binary** | ❌            | ✅5.5ms 5MB NPU336                       | QNN API | [details](https://app.aihub.qualcomm.com/jobs/jpew8mj1p/) |
| **precompiled_qnn_onnx** | ❌          | ✅5.4ms 17MB NPU331                       | ONNX Runtime | [details](https://app.aihub.qualcomm.com/jobs/jpvrek1z5/) |
| **qnn_dlc**            | ✅ 5.4ms 5MB NPU415            | ✅5.0ms 20MB NPU326                 |  QNN API | [details](https://app.aihub.qualcomm.com/jobs/jg9yknvl5/) |

`QNN API/Backend/SDK needs to run within Ubuntu 20.04`  [• You have an Ubuntu 20.04 or WSL2 on Windows with an Ubuntu 20.04 development environment.](https://www.qualcomm.com/developer/software/neural-processing-sdk-for-ai)
