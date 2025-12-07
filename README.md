# Nakhatra-Automation
This project demonstrates Python → MQTT → Home Assistant integration as part of the Nakshatra Automation technical assignment. The system publishes sensor data using MQTT and displays the values in Home Assistant through MQTT sensors.
import paho.mqtt.client as mqtt
import json
import time
student_name = "Jayaseelan I"
unique_id = "42731027"
topic = "home/jayaseelan-2025/sensor"
broker = "192.168.0.113"
port = 1883
temperature = 25
humidity = 60
gas_level = 350
client = mqtt.Client()
client.username_pw_set("jayaseelan", "1234")
client.connect(broker, port)
payload = {
    "student_name": student_name,
    "unique_id": unique_id,
    "temperature": temperature,
    "humidity": humidity,
    "gas": gas_level
}
print("Publishing sensor data...")
client.publish(topic, json.dumps(payload))
print(f"Published to topic: {topic}")
