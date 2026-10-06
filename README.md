# immobilized-beads-
                 RAW WATER
                    │
                    ▼
          ┌──────────────────┐
          │  RAW WATER TANK  │
          └────────┬─────────┘
                   │
                PUMP
                   │
                   ▼
          ┌──────────────────┐
          │   PRE-FILTER     │
          └────────┬─────────┘
                   │
                   ▼
       ┌────────────────────────┐
       │                        │
       │    AGRO-BIOBEADS       │
       │                        │
       │   ● ● ● ● ● ● ● ●     │
       │   ● ● ● ● ● ● ● ●     │
       │   ● ● ● ● ● ● ● ●     │
       │                        │
       └───────────┬────────────┘
                   │
              RETAINER MESH
                   │
                   ▼
           TREATED WATER
                   │
          ┌────────┴─────────┐
          ▼                  ▼
      SENSOR UNIT       SAMPLE BOTTLE
          │
          ▼
        ESP32
          │
          ▼
       OLED/LCD

Sodium alginate
       +
Processed agro-waste
       +
Approved microbial consortium
       ↓
Homogeneous formulation
       ↓
Controlled bead formation
       ↓
Calcium-mediated gelation
       ↓
Washing/conditioning
       ↓
AGRO-BIOBEADS





          ┌───────────────┐
          │     ESP32     │
          └───────┬───────┘
                  │
       ┌──────────┼──────────┐
       │          │          │
       ▼          ▼          ▼
     pH         Turbidity    TDS/EC
   Sensor        Sensor      Sensor
       │          │          │
       └──────────┼──────────┘
                  │
                  ▼
             OLED DISPLAY


====================
  AGRO-BIOBEAD
     REACTOR
====================




#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>

#define SCREEN_WIDTH 128
#define SCREEN_HEIGHT 64

Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, -1);

const int PH_PIN = 34;
const int TURBIDITY_PIN = 35;
const int TDS_PIN = 32;

void setup() {
  Serial.begin(115200);

  Wire.begin(21, 22);

  if (!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) {
    while (true);
  }

  display.clearDisplay();
  display.setTextSize(1);
  display.setTextColor(SSD1306_WHITE);
  display.setCursor(0, 0);
  display.println("AGRO-BIOBEAD");
  display.println("SMART REACTOR");
  display.display();

  delay(2000);
}

void loop() {

  int phRaw = analogRead(PH_PIN);
  int turbidityRaw = analogRead(TURBIDITY_PIN);
  int tdsRaw = analogRead(TDS_PIN);

  // Replace these placeholder conversions
  // with calibration equations for your exact sensors.
  float pH = 7.0;
  float turbidity = turbidityRaw;
  float tds = tdsRaw;

  Serial.print("pH: ");
  Serial.println(pH);

  Serial.print("Turbidity raw: ");
  Serial.println(turbidityRaw);

  Serial.print("TDS raw: ");
  Serial.println(tdsRaw);

  display.clearDisplay();

  display.setCursor(0, 0);
  display.println("AGRO-BIOBEAD");

  display.print("pH: ");
  display.println(pH, 2);

  display.print("Turb: ");
  display.println(turbidity, 1);

  display.print("TDS: ");
  display.println(tds, 1);

  display.display();

  delay(1000);
}




RAW WATER
   │
   ├───────────────┐
   │               │
   ▼               ▼
CONTROL         AGRO-BIOBEAD
COLUMN           COLUMN
   │               │
   ▼               ▼
CONTROL         TREATED
WATER           WATER




        POLLUTED WATER
              ↓
        AGRO-BIOBEADS
              ↓
   ADSORPTION + BIOLOGICAL
          TREATMENT
              ↓
        TREATED WATER
              ↓
     QUALITY MONITORING
              ↓
          REUSABLE

pH       : 7.21
Turbidity: 18 NTU
TDS      : 245 ppm

STATUS: TREATMENT
====================


====================
   TREATED WATER
====================

pH       : 7.10
Turbidity: 7 NTU
TDS      : 230 ppm

STATUS: COMPLETE
====================