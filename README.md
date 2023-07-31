# GNSS_D300_driver_dora

run driver: 

sudo chmod 777 /dev/ttyUSB*

dora up

A terminal run: RUST_LOG=debug dora start gnssD300_nmea_driver_dora.yaml  --attach --hot-reload

Another terminal run: dora logs ******


------------------------------------------------------------------------------------------------------------

完成了对应ros2的NavSatFix、QuaternionStamped、TwistStamped速度部分的消息发布。

1.nmea_getSentence_driver_dora：打开串口，读取数据进行校验，校验无误后发送到nmea_publishSentence_driver_dora。
在nmea_getSentence_driver_dora.py中默认下值，连接串口后根据情况更改:
serial_port = '/dev/ttyUSB1'
serial_baud = 115200

2.nmea_publishSentence_driver_dora完成对输入进行NMEA句子格式的判断并解析，解析无误，以序列化后的类send_out到nmea_subscribeSentence_driver_dora。

3.nmea_subscribeSentence_driver_dora对消息类型进行判别，并输出解析后的数据。

-------------------------------------------------------------------------------------------------------------
