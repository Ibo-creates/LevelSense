#include <Adafruit_Sensor.h>
#include <Adafruit_MPU6050.h> 
#include <Wire.h>
#include <math.h>
#include <WiFi.h>

const char* ssid = "LevelSense";
const char* password = "ibocreates";

String currentmode = "both";//Intially the button is shown as both, so the user needs to select between roll and pitch.
String bgcolor = "Red";

WiFiServer server(80);
Adafruit_MPU6050 mpu;

#define I2C_SDA 8
#define I2C_SCL 9

void setup() {
  Serial.begin(115200);
  Wire.begin(I2C_SDA, I2C_SCL);
  mpu.begin();
a
  WiFi.softAP(ssid , password);
  IpAddress IP = WiFi.softAPIP();
  Serial.print("Ap Ip adres: ");
  Serial.println(IP);

  server.begin();
}

void loop() {
  sensors_event_t a, g, temp;
  mpu.getEvent(&a, &g , &temp);

  float x = a.acceleration.x;
  float y = a.acceleration.y;
  float z = a.acceleration.z;

  float roll = atan2(y, z) * 180 / PI;
  float pitch = atan2(-x, sqrt(y * y + z * z)) * 180 / PI;

  if(currentmode == "roll"){
    if(abs(roll) < 1) bgcolor = "Green";
    else bgcolor = "Red";  
  } else if(currentmode == "pitch"){
    if(abs(pitch) < 1) bgcolor = "Green";
    else bgcolor = "Red";  
  } else {
    if(abs(roll) < 1 && abs(pitch) < 1) bgcolor = "Green";
    else bgcolor = "Red";  
  }

  WiFiClient client = server.available();
  if (client) {
    String currentline = "";
    while (client.connected()) {
      if (client.available()) {
        char c = client.read();

        if (c == '\n') {
          if (currentline.length() == 0) {
            client.println("HTTP/1.1 200 OK");
            client.println("Content-type:text/html");
            client.println();
            client.println("<html>");
            client.println("<head>");
            client.println("<title>LevelSense</title>");
            client.println("<meta http-equiv='refresh' content='0.2'>");
            client.println("</head>");
            client.println("<body style='background-color:");
            client.print(bgcolor);
            client.println("; color: white; text-align: center; font-family: Arial, sans-serif;'>");
            client.println("<h1 style='font-size: 28px; margin-top: 20px;'>LevelSense</h1>");
            client.println("<div style='margin-top: 25vh; font-size: 70px; font-weight: bold;'>");
            
            if (currentmode == "roll") {
              client.print("Roll: ");
              client.print(roll);
            } else if (currentmode == "pitch") {
              client.print("Pitch: ");
              client.print(pitch);
            } else {
              client.print("Roll: ");
              client.print(roll);
              client.println("<br>");
              client.print("Pitch: ");
              client.print(pitch);
            }
            client.println("</div>");
            client.println("<div style='position: fixed; bottom: 20px; right: 20px; text-align: right; background: rgba(0,0,0,0.2); padding: 10px; border-radius: 5px;'>");
            client.println("<form action='/change' method='get' style='margin: 0;'>");
            client.println("<select name='axis' style='padding: 5px; font-size: 14px;'>");
            
            client.print("<option value='roll'");  if(currentmode=="roll")  client.print(" selected"); client.println(">Roll Only</option>");
            client.print("<option value='pitch'"); if(currentmode=="pitch") client.print(" selected"); client.println(">Pitch Only</option>");
            client.print("<option value='both'");  if(currentmode=="both")  client.print(" selected"); client.println(">Both Axes</option>");
            
            client.println("</select><br>");
            client.println("<input type='submit' value='Set' style='margin-top: 5px; width: 100%; font-size: 12px;'>");
            client.println("</form>");
            client.println("</div>");
            
            client.println("</body>");
            client.println("</html>");
            break;
          } else {
            if (currentline.indexOf("GET /change?axis=roll") >= 0) currentmode = "roll";
            else if (currentline.indexOf("GET /change?axis=pitch") >= 0) currentmode = "pitch";
            else if (currentline.indexOf("GET /change?axis=both") >= 0) currentmode = "both";
            currentline = "";
          }
        } else if (c != '\r') {
          currentline += c;
        }
      }
    }
    client.stop();
  }

  Serial.print("Roll: ");// Added thse for debugging and making sure that the levelsense is transmitting data incase of any issue on the webpage side. 
  Serial.print(roll);
  Serial.println(" Pitch: ");
  Serial.print(pitch);
  delay(150);
}
