### Camera streaming(Open-CV + Flask) and display on different threads with safe synchronization
```python
pip install requirements.txt

```
### Run Server
```python
python app.py

```
#### Use Built-in Webcam of Laptop
##### Put Zero (O) in cv2.VideoCapture(0)
```python
cv2.VideoCapture(0)
 
```
#### Use Ip Camera/CCTV/RTSP Link
```python
cv2.VideoCapture('rtsp://username:password@camera_ip_address:554/user=username_password='password'_channel=channel_number_stream=0.sdp')  

 ```
####  Example RTSP Link
```python
cv2.VideoCapture('rtsp://mamun:123456@101.134.16.117:554/user=mamun_password=123456_channel=0_stream=0.sdp')

```
#### Change Channel Number to Change the Camera
```python
cv2.VideoCapture('rtsp://mamun:123456@101.134.16.117:554/user=mamun_password=123456_channel=1_stream=0.sdp')

```
#### Display the resulting frame in browser
```python
cv2.imencode('.jpg', frame)[1].tobytes()

```   
#### Display the resulting frame in window
##### Write this end of the line [camera.py](/camera.py)
```python
if __name__ == "__main__" :
    cap = CameraStream().start()
    while True :
        frame = cap.read()
        cv2.imshow('webcam', frame)
        if cv2.waitKey(1) == 27 :
            break
    cap.stop()
    cv2.destroyAllWindows()      
``` 
#### Credit
 - Multi Thread Use From [allskyee's](https://github.com/allskyee)  [Open-CV Multi-Thread Gist](https://gist.github.com/allskyee/7749b9318e914ca45eb0a1000a81bf56)
