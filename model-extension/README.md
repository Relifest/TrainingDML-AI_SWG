# Deep Learning Model Extension of TrainingDML-AI

## 1. Abstract
The deep learning model extension (model-extension) of TrainingDML-AI aims to develop the UML model and encodings to describe geospatial deep learning models. The model-extension will align with TrainingDML-AI and OGC standards baseline to facilitate the sharing, exchange, reusability, and inference of models in the web environment.

## 2. Scope of Work
Deep learning has significantly contributed to geospatial analysis and revolutionized how we understand and extract information from geospatial data. Nowadays, abundant deep learning models are trained daily to accomplish various geospatial tasks, such as land cover and land use mapping, change detection, road network extraction, geospatial data fusion, etc. However, the information of most models has not been described and recorded standardized, which brings difficulties to the sharing and reusing of models and is not conducive to interoperability and reusability. Hence, the model-extension is proposed to develop the UML model to standardize the deep learning framework, neural network, optimization method, training data, tasks, quality, etc., of geospatial deep learning models so that the models can be shared and managed in a unified framework. 
The model-extension will undertake the following work actions around geospatial deep learning models:
- Design the UML model of geospatial deep learning models, maximize the findability, interoperability, and reusability;
- Define the description of neural network and optimization method of models;
- Define the description of model quality(e.g., performance metrics, computational complexity, generalization, robustness);
- Define the JSON schema for encoding geospatial deep learning models;
- Best practices for documenting, storing, evaluating, managing, and sharing the geospatial deep learning models.

## 3. Normative References
The following normative documents contain provisions that, through reference in this text, constitute provisions of this document. For dated references, subsequent amendments to, or revisions of, any of these publications do not apply. For undated references, the latest edition of the normative document referred to applies.

[ISO 19157-1 Geographic information — Data quality — Part 1: General requirements.](https://www.iso.org/standard/78900.html)

## 4. UML Model
The UML model is the normative definition of the TDML model-extension Conceptual Model. The figures in this section were software generated from the UML model. As such, this section provides a normative representation of the TDML model-extension Conceptual Model.

### 4.1	Overview of the UML model
The UML model is presented with core concepts in Figure 1. The following describes the core concepts:
- AI_DeepLearningModel: This concept represents a deep learning model;
- AI_NeuralNetwork: This concept describes the neural network of the deep learning model;
- AI_Optimization: This concept describes the information about how to train the deep learning model;
- AI_ModelQuality: This concept describes the quality of the deep learning model;
- AI_TrainingDataset: From TrainingDML-AI;
- AI_Task: From TrainingDML-AI.

<div align=center> 
<img width="600" src="UML/Conceptual Model.svg"/>
</div>
<div align=center> Figure 1. Core concepts.</div>

The full overview of concrete classes and attributes are presented in Figure 2. Concepts related to the EO AI/ML applications are defined as classes extended from abstract classes. Each core concept with related classes will be described in the rest subsections.

<div align=center>
<img width="900" src="UML/UML Model.svg"/>
</div>
<div align=center> Figure 2. UML model</div>

### 4.2 AI_DeepLearningModel
A deep learning model is represented as AI_AbstractDeepLearningModel. A set of basic attributes are defined for AI_AbstractDeepLearningModel. These include the identification, name for findability; providers, references, citations, and license for copyright; inputs, outputs, deep learning framework, save format, dependencies, and resources for reusability; version, created time, and updated time for update. These basic attributes can also be seen as a minimum set of metadata to define a simple payload.

#### 4.2.1 Class Definitions
Table 1. Classes defined in AI_DeepLearningModel
| **Name**                         | **Description**                                                  |
| ---------------------------- | ------------------------------------------------------------ |
| AI_AbstractDeepLearningModel | AI_AbstractDeepLearningModel defines the basic concepts and components of a deep learning  model. |
| AI_EODeepLearningModel       | AI_EODeepLearningModel describes attributes  specific to a EO deep learning model. |

Table 2. Data types defined in AI_DeepLearningModel
| **Name**                           | **Description**                                                  |
| ------------------------------- | ------------------------------------------------------------ |
| AI_AbstractIOType  \<\<DataType>> | AI_AbstractIOType  defines the basic concepts of inputs and outputs of the  deep learning model. |
| AI_EOIOType  \<\<DataType>>       | AI_EOIOType defines attributes of inputs and outputs specific to the EO deep learning  model. |

#### 4.2.2 Data Dictionary
Table 3. Attributes of AI_AbstractDeepLearningModel (Class)
| **Attribute**         | **Value type and multiplicity** | **Definition**                                               |
| --------------------- | ------------------------------- | ------------------------------------------------------------ |
| id                    | CharacterString  [1..1]         | Identification  of the deep learning model.                  |
| name                  | CharacterString  [1..1]         | Name  of the deep learning model.                            |
| providers             | CharacterString  [0..*]         | People  or organizations who provide the deep learning model. |
| deepLearningFramework | CharacterString  [1..*]         | Deep learning  framework of the deep learning model. For example PyTorch, TensorFlow. |
| saveFormat            | CharacterString  [1..*]         | Save  format of the deep learning model. For example ONNX, TensorRT. |
| inputs                | AI_AbstractIOType[0..*]         | The  information of the inputs of the deep learning model.   |
| outputs               | AI_AbstractIOType[1..*]         | The  information of the outputs of the deep learning model.  |
| modelURL              | URL[1..*]                       | URLs of the deep learning model.                             |
| version               | CharacterString  [0..1]         | Version  number of the deep learning model.                  |
| createdTime           | DateTime  [0..1]                | Time  when the deep learning model was created.              |
| updatedTime           | DateTime  [0..1]                | Time  when the deep learning model was updated.              |
| softwareDependencies  | CharacterString  [0..*]         | Software  requirement that the deep learning model relies on to function correctly. |
| hardwareDependencies  | CharacterString  [0..*]         | Hardware  requirement that the deep learning model relies on to function correctly. |
| references            | CharacterString  [0..*]         | The  literatures that the deep learning model is referenced. |
| citations             | CharacterString  [0..*]         | Citations  when using the deep learning model.               |
| resources             | CharacterString  [0..*]         | Additional  resources related to the deep learning model, for example GitHub link. |
| license               | CharacterString  [1..1]         | License  description of the deep learning model.             |
| description           | CharacterString  [0..*]         | Other  description of the deep learning model.               |

Table 4. Attributes of AI_EODeepLearningModel (Class)
| **Attribute** | **Value type and multiplicity** | **Definition**                                               |
| ------------- | ------------------------------- | ------------------------------------------------------------ |
| inputs        | AI_EOIOType[0..*]               | The  information of the inputs of the EO deep learning model. |
| outputs       | AI_EOIOType[1..*]               | The information  of the outputs of the EO deep learning model. |

Table 5. Attributes of AI_AbstractIOType (DataType)
| **Attribute** | **Value type and multiplicity** | **Definition**                                               |
| ------------- | ------------------------------- | ------------------------------------------------------------ |
| id            | CharacterString  [1..1]         | Identification  of the input/output data.                    |
| dataType      | CharacterString  [1..1]         | Data  type of the input/output data, for example image, text, video. |
| dataFormat    | NamedValue[1..1]                | Data  format of the input/output data, for example the NumPy array. |
| description   | CharacterString[0..*]           | Other  description of the input/output data.                 |

Table 6. Attributes of AI_EOIOType (DataType)
| **Attribute**     | **Value type and multiplicity** | **Definition**                                               |
| ----------------- | ------------------------------- | ------------------------------------------------------------ |
| meanNormalization | Float[0..*]                     | The  mean used to normalize the EO input data.               |
| stdNormalization  | Float[0..*]                     | The standard  deviation used to normalize the EO input data. |
| dataSources       | CI_Citation[0..*]               | Citation  of data sources.                                   |
| extent            | EX_Extent[0..1]                 | Spatial  extent of the EO input data.                        |
| bands             | MD_Bands[0..*]                  | Description  of the image bands in the EO input/output data. |
| imageSize         | CharacterString[0..1]           | Size  of the EO input/output data.     

### 4.3 AI_NeuralNetwork
The neural network of a deep learning model is represented as AI_NeuralNetwork. The details of the neural network architecture and parameters are described in AI_NeuralNetwork for model reproduction.

#### 4.3.1 Class Definitions
Table 7. Classes defined in AI_NeuralNetwork
| **Name**         | **Description**                                              |
| ---------------- | ------------------------------------------------------------ |
| AI_NeuralNetwork | AI_NeuralNetwork defines the concepts of neural network of a deep learning model. |

#### 4.3.2 Data Dictionary
Table 8. Attributes of AI_NeuralNetwork (Class)
| **Attribute** | **Value type and multiplicity** | **Definition**                                           |
| ------------- | ------------------------------- | -------------------------------------------------------- |
| architecture  | CharacterString  [1..*]         | Neural  network architecture of the deep learning model. |
| parameters    | CharacterString  [0..*]         | The  number of parameters of the neural network.         |

### 4.4 AI_Optimization
AI_Optimization records the attributes needed to train the neural network.

#### 4.4.1 Class Definitions
Table 9. Classes defined in AI_Optimization
| **Name**        | **Description**                                              |
| --------------- | ------------------------------------------------------------ |
| AI_Optimization | AI_Optimization defines the concepts to train the neural network. |

#### 4.4.2 Data Dictionary
Table 10. Attributes of AI_Optimization (Class)
| **Attribute**        | **Value type and multiplicity** | **Definition**                                               |
| -------------------- | ------------------------------- | ------------------------------------------------------------ |
| optimizer            | CharacterString[1..1]           | The optimization  algorithms to minimize the objective function during the training process,  for example stochastic gradient descent. |
| objectiveFunction    | CharacterString[1..*]           | A  mathematical function that quantifies the difference between predicted and  actual values. |
| numberOfEpochs       | Int[0..1]                       | Number  of epochs, where an epoch is a complete iteration through the entire training  dataset for training. |
| batchSize            | Int[0..1]                       | Batch  size defines the number of samples used in one iteration to train a neural  network. |
| learningRate         | CharacterString[0..1]           | A parameter  in the optimizer that determines the step size at each iteration. |
| hardwareDependencies | CharacterString[0..*]           | Hardware  requirement to train the deep learning model.      |
| pretrainedModels     | CharacterString[0..*]           | Pretrained  models that the training process relies on.      |
| hyperparameters      | CharacterString[0..*]           | Other hyperparameters  to train the deep learning model.     |

### 4.5	AI_ModelQuality
The quality of a deep learning model refers to its performance and effectiveness in solving a specific task or problem. Evaluating the quality of a deep learning model involves considering various aspects and metrics. Here are some key factors and elements that contribute to assessing the quality of a deep learning model: accuracy, computational complexity, generalization, robustness, fairness, and explainability. AI_ModelQuality records these elements to express the quality of the deep learning model. The quality description of the deep learning model can leverage the quality elements defined in QualityElement from ISO 19157. 

The data quality element of ISO 19157 is described by a reference to a quality measure, an evaluation method, a quality result, and a metaquality element. These are shown in Figure 3. Measure reference provide an identifier of a measure fully described elsewhere. Evaluation method describes those procedures and methods which are applied to the geographic data to arrive at a data quality result. Quality result is provided for each data quality element. This could be a quantitative result, a conformance result, a descriptive result or a coverage result. A metaquality element is described by the same descriptors as for the quality element: measure, evaluation method and result.

<div align=center>
<img width="700" src="UML/QualityElement of ISO 19157.png"/>
</div>
<div align=center> Figure 3. Data quality element descriptors.</div>

#### 4.5.1 Class Definitions
Table 11. Classes defined in AI_ModelQuality
| **Name**                | **Description**                                              |
| ----------------------- | ------------------------------------------------------------ |
| AI_AbstractModelQuality | AI_AbstractModelQuality defines the basic quality elements of a deep learning model. |
| AI_EOModelQuality       | AI_EOModelQuality describes quality  elements specific to a EO deep learning model. |

#### 4.5.2 Data Dictionary
Table 12. Attributes of AI_AbstractModelQuality (Class)
| **Attribute**           | **Value type and multiplicity** | **Definition**                                               |
| ----------------------- | ------------------------------- | ------------------------------------------------------------ |
| performanceMetrics      | QualityElement[1..*]            | Accuracy  of the deep learning model.                        |
| computationalComplexity | QualityElement[0..*]            | How  efficiently a deep learning model performs tasks while utilizing  computational resources such as CPU/GPU, memory, and energy. |
| generalization          | QualityElement[0..*]            | The  ability to perform well on data it has never seen before. |
| robustness              | QualityElement[0..*]            | The  ability to maintain their level of performance, as intended by their  developers, under any condition and circumstances. |
| fairness                | QualityElement[0..*]            | Equitable  and unbiased treatment of different individuals or groups. |
| explainability          | QualityElement[0..*]            | The  property that the important factors influencing a decision can be expressed  in a way that humans can understand. |
| isPretrainedModel       | Bool[0..*]                      | Whether  the deep learning model can be used as a pre-trained model. |
| applicationScope        | CharacterString[0..*]           | A  complementary description of the deep learning model application scope. |

Table 12. Attributes of AI_EOModelQuality (Class)
| **Attribute**          | **Value type and multiplicity** | **Definition**                                               |
| ---------------------- | ------------------------------- | ------------------------------------------------------------ |
| spatialGeneralization  | QualityElement[0..*]            | The  ability to perform well on data from unseen geographic regions. |
| temporalGeneralization | QualityElement[0..*]            | The  ability to perform well on data from unseen time period. |

### 4.6	AI_TrainingDataset
AI_TrainingDataset records the dataset needed to train the deep learning model. The training dataset description can leverage the AI_AbstractTrainingDataset and AI_EOTrainingDataset defined in TrainingDML-AI.

### 4.7	AI_Task
AI_Task refers to a specific problem or objective addressed using deep learning techniques and models. The task description can leverage the AI_AbstractTask and AI_EOTask defined in TrainingDML-AI.

## 5. Use Cases
A collection of some encoded deep learning models:
|Model Name|Training Dataset|Description|JSON|Download|
|-|-|-|-|-|
|UPerNet_LULC|Five-Billion-Pixels|A land use land cover classification model based on UPerNet with 25 classes.|[UPerNet_LULC.json](use-cases/UPerNet_LULC.json)|[UPerNet_LULC.onnx](https://drive.google.com/file/d/1AcsTRsgHAwOROfq1qsa709kdKHleFmE0/view?usp=drive_link)|
|CropLandExtraction_GF2|-|Crop land extraction model on GF-2 images.|[CropLandExtraction_GF2.json](use-cases/CropLandExtraction_GF2.json)|[CropLandExtraction_GF2.onnx](https://drive.google.com/file/d/1x7s3LWbHln2bj_X54jU9Il7Wi_mB5mZu/view?usp=sharing)|




