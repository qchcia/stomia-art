# Research Project CSIT 2021-2022

# Project 6: Preparation and preprocessing photo and video materials for medical photogrammetry

* Supervisor:
    * dr hab. inż. Anna Fabijańska, prof. ucz.
* Author:
    * Stanisław Puławski, 239111, IFE CSIT 2021

    
### Description:
Photogrammetry is the science and technology of obtaining reliable information about physical objects and the environment. Using a lot of images, we can reconstruct 3d model of the photographed object. The quality of a mapped object is dependent on numerous factors, for instance: Lighting, quantity, and quality of input images, camera trajectory, the distance between object and camera.

The goal of the research project is to find the best way to collect and preprocess input material for photogrammetry. The method should be easy to reproduce and cannot generate large amounts of data. Last but not least, the comfort of users of the process should be taken into consideration. The process should be optimal for both parts of the process: preprocessing on the client-side and processing and 3d model creation on the server-side.

source: `https://ife.edu.p.lodz.pl/mod/reservation/view.php?id=22641`

### the purpose of the project
The project aims to accelerate and simplify the process of making 3d models

### How it works?
The algorithm presented in the document allows for the automation of the process of preparing the input data for the photogrammetry program.

### What the algorithm does?
Alghoritm received video material on input and return packages with photo which are ready to upload to photogrammetry program.

### How the algorithm facilitates work with files
Algorithm do several tasks:
1. Slice video to serie of images
2. Reduce framerate
3. Aruco detection
4. Get statistics data about Arucos from every image and save as collection
5. Draw metadata on temporary files
6. Presents charts and data frames with metadata
7. Sort and group photo, next choose the best


### Advantages and disadvantages of the solution
#### Advantages:
* Automates tasks
* Help to download video from camera (smartphone)
* Reduce time for creation 3D model
* Save space on disk - optimized bundle with several images is lighter than whole video or sliced video
* Allows to judge quality of input material before photogrammetry process
* Support protogrametry program with focuse on object to scan
* We can skip unnecessary environmental data (like objects and things near scanned object)

#### Disadvantages
* During reduce frames we can lose high quality and important frames
* Process is lossy and irreversible (if we don't save input video mateiral)
* When we reduce quantity of samples, output model probably will be in lower quality

# Conclusions

## QRcodes vs Aruco
QRcodes are harder to detect than Aruco. At firsts test with QRcode my alghoritm detect very small amount of detected QRcodes. Aruco detection is simpler and faster.


QR code                    |  Aruco code               
:-------------------------:|:-------------------------:
![8-qr.png](attachment:af31e388-7be2-4e6e-bc9c-3001c4a45c2e.png)  |  ![9-aruco.jpg](attachment:dd9b0da2-0b89-4f12-9035-263112d7c8c4.jpg)



## Markers recognition vs object recognition

During this project we are focused on medical photogrammetry. We paid special attention to visualization of the patients stoma. We decided to not detect stoma as object, instead of markers around them. Object detection alghoritm may confuse stoma with birthmarks or scars. Next advantage of markers is reference point: We know dimensions of markers, so we can measure every part of 3D model based on size of markers. Moreover, recognition of markers can help us to detemine orientation of the photo, what is important in process of 3D reconstruction.

## Crop image
Cropping images leading to minimize size of file and skipping unnecessary environmental data allows us to create 3D model on a faster and more accurate way. Received model is pure (?) and not so blurred as model received with unnecesarry surroundings.

QR code                    |  Aruco code               
:-------------------------:|:-------------------------:
![6.png](attachment:89773b65-9902-4cac-8afc-1c9d409e3867.png) | ![7.png](attachment:6c14600a-81e2-4c63-a5c3-a840a4add8c7.png)


## Select the best images

## How to run algorithm
For testing purpoise I prepare GUI using Jupyter Notebook IPy widgets
![10.png](attachment:1aa56a9b-21f1-4bd6-8858-7fc756261491.png)

# WAŻNE
### Parametry do zbadania podczas tworzenia modeli 3d:
1. czas powstawania modelu - aktualnie max 3 minuty, ale jeśli możesz to pominąć to lepiej pomiń
2. Jakośc modelu
3. Jakośc tła
4. Jakosc tekstur
5. Jakość kolorów
6. Jakość oszorowania 3D
7. Wielkość (np. w kiloBajtach) powstałego modelu - tu wszystko zależy od rozszerzenia
8. Poprawność wykonania modelu
9. Możliwośc wykonania modelu (jeżeli model się nie stworzył to dlaczego?) - jaka dotychczas nie wszystkie klatki mają określoną orientację i Zephyr je odrzuca
10. Wpływ przycinania tła na jakośc skanowania
11. Wpływ parametrów:
* "skipFrames"
* "scale"
* "cnt of images on output"


## Paczki ze zdjęciami
W paczce znajdują się zdjęcia w różnych opcjach:
* out-all-raw - just sliced images
* out-all-tag - all sliced images with tags and metadata
* out-best-raw - selected raw images
* out-best-tag - selected images with tags and metadata
* out-best-crop - selected raw CROP images
oraz plik testowy z danymi o danej paczce.

Dobrze by było odpowiedzieć na kilka pytań:
* Na podstawie której paczki najlepiej generuje się modele? - to się zrobi na tych obiektach rzeczywistych
* Czy przycinanie ma sens? Czy wybrane best-raw sa ok? Czy nie jest ich za mało? - jest za mało
* Jaki jest czasy wykonywania modelu dla poszczególnej paczki? - to też wartościowo będzie ocenić na dobrym modelu
* Dałem jedną paczkę w wyższej rozdzielczości, czy ona sprawuje się lepiej?





```python

```
