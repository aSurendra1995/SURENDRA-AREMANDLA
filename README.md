# SURENDRA-AREMANDLA
Automatic car wiper using Rain Sensor and sensor diagnosis using Arduino 

#define m0 A0
#define E1 10  // Enable Pin for motor 1
#define I1 8  // Control pin 1 for motor 1
#define I2 9  // Control pin 2 for motor 1
void setup() {
  // put your setup code here, to run once:
   pinMode(m0, INPUT);
   pinMode(E1, OUTPUT);
    pinMode(I1, OUTPUT);
    pinMode(I2, OUTPUT);
   Serial.begin(9600);

}

void loop() {
  // put your main code here, to run repeatedly:
    float rain = analogRead(m0);
    rain = ((rain*3.3)/1023.0);
    Serial.println('rain sensor value :"');
    Serial.print(rain);
    if(rain >=3.3)
    {
      Serial.println("sensor fault\n");
    }
    
  if(rain < 2)
  {
     analogWrite(E1, 153); // Run in half speed
    digitalWrite(I1, HIGH);
    digitalWrite(I2, LOW);
    delay(10000);

    // change direction

    digitalWrite(E1, LOW);
    delay(200);
    analogWrite(E1, 153);  
    digitalWrite(I1, LOW);
    digitalWrite(I2, HIGH);
    delay(10000);
  }
}
