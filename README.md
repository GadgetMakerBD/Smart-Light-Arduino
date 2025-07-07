# 💡 স্মার্ট লাইট সিস্টেম (Arduino প্রজেক্ট)

এই প্রজেক্টে আমরা তৈরি করেছি একটি স্মার্ট লাইট সিস্টেম যা **অন্ধকারে নিজে থেকে লাইট চালু করে** এবং **আলো থাকলে নিজে থেকে বন্ধ হয়ে যায়।**  
এই প্রজেক্টে ব্যবহার করা হয়েছে Arduino Uno, LDR সেন্সর এবং ৫V রিলে মডিউল।

---

## 🧰 ব্যবহৃত কম্পোনেন্টসমূহ:

- Arduino Uno R3 SMD  
- LDR Light Sensor Module (Digital)  
- 5V Relay Module  
- Jumper Wires (6টি)  
- AC LED Light  
- Plug ও Light Holder

---

## ⚙️ সার্কিট সংযোগ:

🔹 **LDR সেন্সর:**
- VCC → Arduino 5V  
- GND → Arduino GND  
- OUT → Arduino Digital Pin 8

🔹 **Relay Module:**
- VCC → Arduino 5V  
- GND → Arduino GND  
- IN → Arduino Digital Pin 7

🔹 **AC Light:**
- Live → Relay এর COM (Common)  
- NO (Normally Open) → Light  
- Light এর অন্য প্রান্ত → AC Neutral

⚠️ **সতর্কতা:** AC লাইনের সংযোগ দেওয়ার সময় অবশ্যই বিদ্যুৎ সংযোগ বিচ্ছিন্ন করে কাজ করবেন।

---

## 📄 কোড ব্যাখ্যা:

Arduino কোডটি LDR সেন্সর থেকে আলো পাওয়া যাচ্ছেনা বুঝলে রিলে চালু করে এবং লাইট অন করে। আলো থাকলে রিলে বন্ধ হয় এবং লাইট বন্ধ হয়ে যায়।

```cpp
#define Sensor 8
#define RELAY_PIN 7

void setup() {
  pinMode(Sensor, INPUT);
  pinMode(RELAY_PIN, OUTPUT);
  digitalWrite(RELAY_PIN, HIGH);
}

void loop() {
  int status_sensor = digitalRead(Sensor);
  if (status_sensor == 1) {
    digitalWrite(RELAY_PIN, LOW);
  } else {
    digitalWrite(RELAY_PIN, HIGH);
  }
  delay(100);
}
