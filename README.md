# Cylinder-Tracking

# Detector de pipetas de gas de 9, 15, 18 y 45 lb empleando Deep learning

Se realiza un prototipo para una primera aproximación detectando los cilindros de diferentes dimensiones empleando deep learning, prototipo realizado por Intecol para la empresa Gasco. Se muestran las imágenes de los cilindros correspondientes.

<img src="ImagenesMuestra/Pipetas.png" alt="" style="height:400px"></img> 

El video inicial fue grabado por las cámaras de la empresa Gasco, posterior a esto el video fue dividido en partes más pequeñas, para finalmente obtener varias imágenes para realizar un entrenamiento con el modelo Yolov5x en Python, las etiquetas fueron hechas en Roboflow.

Se ha de tener en cuenta que las carpetas valid y train deben estar ubicadas en la ruta *Cylinder-Tracking/Codigo/Codigo/*. Las carpetas runs y data deben estar en la ruta *Cylinder-Tracking/Codigo/Codigo/yolov5/*. Estas carpetas se encuentran en Drive.

El repositorio original de Yolo tomado como base para la realización del prototipo es el siguiente *https://github.com/ultralytics/yolov5.git*. Ahora entrando en detalle, el código requiere dos etapas; una de entrenamiento, la cual da como resultado el archivo best.pt en la ruta *Cylinder-Tracking/Codigo/Codigo/yolov5\runs\train\yolov5x_results2\weights*, el comando necesario para realizar el entrenamiento es el siguiente: 
*python train.py --img 416 --batch 16 --epochs 60 --data '../data.yaml' --cfg ./models/yolov5x.yaml --name yolov5x_results  --cache*

Posterior al entrenamiento se realiza una validación para imágenes , el comando es el siguiente:
*python detect.py --weights runs/train/yolov5x_results/weights/best.pt --img 416 --conf 0.4 --source ../valid/images*
En caso de querer realizar el análisis sobre un video:
*python detect.py --weights runs/train/yolov5s_results/weights/best.pt --img 416 --conf 0.4 --source ../valid/video/video.mp4*

Se realizaron varias pruebas, obteniendo la mayor precisión con el modelo Yolov5x.
