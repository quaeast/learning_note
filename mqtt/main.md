# MQTT

```bash
# install
sudo apt install mosquitto
sudo apt install mosquitto-clients
# publish
mosquitto_pub -h quaeast.cn -t "hello"  -m  "hello mqtt"
# subscribe
mosquitto_sub -h quaeast.cn -t  "fangzidong"  -v
```