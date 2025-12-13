# Smart Greenhouse System for Optimizing Crop Growth Conditions

An Automated Greenhouse Environment Control System for Precision Agriculture

## Banner Image

![Smart Greenhouse System](docs/greenhouse_main.jpg)

## 1. Overview

The Smart Greenhouse System is an automated environmental control platform designed to optimize crop growth conditions through real-time monitoring and intelligent actuation. Built using Arduino microcontrollers, a comprehensive sensor array, and automated control mechanisms, the system maintains ideal growing conditions while eliminating the need for constant manual supervision.

The project integrates embedded systems, precision agriculture principles, IoT sensor networks, and automated control theory into a practical, user-configurable solution that supports multiple crop types across different growth stages.

## 2. Problem Statement (African Context)

In Nigeria and across Africa, greenhouse farming faces unique challenges that limit agricultural productivity and food security:

* **Manual Monitoring Burden**: Traditional greenhouses require constant human presence to monitor temperature, humidity, soil moisture, and other parameters - a labor-intensive and impractical approach for small-scale farmers
* **Inconsistent Growing Conditions**: Manual control methods cannot maintain the precise environmental conditions required for optimal crop growth, leading to reduced yields and crop failures
* **Limited Technical Accessibility**: Commercial smart greenhouse systems ($5,000-$20,000+) are completely absent from African markets due to prohibitive costs and dependence on internet infrastructure
* **Climate Variability**: Nigeria's tropical climate with unpredictable rainfall and temperature fluctuations makes consistent crop production extremely challenging without automated environmental control
* **Water Resource Inefficiency**: Manual irrigation leads to significant water wastage through over-watering or inconsistent application, a critical issue in water-scarce regions
* **Knowledge Gap**: Farmers lack access to precision agriculture tools and training that could help them optimize resource use and maximize yields
* **High Post-Harvest Losses**: Without controlled environments, crops are vulnerable to diseases, pests, and environmental stress, leading to losses of 30-50% in some regions
* **Educational Limitations**: African universities and agricultural research institutions need affordable greenhouse automation platforms for teaching and research, but commercial solutions are unavailable locally

Commercial greenhouse automation systems are designed for Western markets and fail to address African realities: complete absence in local markets, astronomical costs relative to farmer incomes, total dependence on internet connectivity (often unavailable in rural areas), lack of local technical support, and no adaptation to tropical agricultural conditions. There is an urgent need for affordable, locally-buildable, offline-capable greenhouse automation systems that can be maintained and repaired using locally available skills and components.

## 3. Solution Summary

This project develops a fully functional smart greenhouse prototype that brings precision agriculture technology to Africa through locally accessible components and offline operation. Where commercial solutions are non-existent, this demonstrates that professional-grade environmental control can be achieved affordably using Arduino microcontrollers and standard electronic components.

### System Architecture

The system employs a dual-microcontroller architecture that separates sensing from control, ensuring robust and responsive operation:

**Microcontroller 1 (MCU1) - Sensing Node:**
* Continuous real-time data acquisition from all sensors
* Soil moisture monitoring (capacitive sensor)
* Soil pH measurement (analog probe)
* Soil temperature sensing
* Atmospheric temperature and humidity monitoring (DHT22)
* UV light intensity measurement
* Liquid pH monitoring for irrigation water quality
* Live data display on LCD1
* Serial data transmission to MCU2

**Microcontroller 2 (MCU2) - Control Node:**
* Receives sensor data from MCU1 via UART
* Stores user-configured threshold values for each crop
* Implements decision logic through continuous comparison
* Controls actuators via relay modules
* Displays system status and thresholds on LCD2
* Accepts user input through 4×4 keypad
* Manages automated irrigation, ventilation, and lighting

### Key Solution Components

**Hardware Platform:**
* 3x Arduino Uno microcontrollers (ATmega328P)
* Dual 12V 7Ah SLA batteries (separate control and actuator power)
* 6x LM2596 voltage regulators for stable power distribution
* Modular sensor suite and relay-driven actuators
* Total material cost: ~₦450,000 (~$300 USD)

**Sensor Array:**
* Soil moisture sensor (capacitive, corrosion-resistant)
* Soil pH sensor (analog probe, 3-9 pH range)
* Liquid pH sensor (pH-4502C with E201-BNC electrode)
* DHT22 temperature/humidity sensor (-40 to 80°C, 0-100% RH)
* SENS43UV ultraviolet sensor (240-370 nm)
* All sensors powered through regulated 5V rails

**Actuator System:**
* 2x 5V DC water pumps (irrigation control)
* 12V DC cooling fan (temperature regulation)
* 12V UV LED strip (supplemental lighting, 395-405 nm)
* NEMA 17 stepper motor (automated vent control)
* All actuators controlled via 5x one-channel relay modules

**User Interface:**
* Dual 16×2 LCD displays with I²C interface
* LCD1: Real-time sensor readings
* LCD2: Threshold values and actuator status
* 4×4 matrix keypad for parameter input
* No internet, smartphone, or computer required

### Mechanical Design

![Greenhouse Structure](docs/greenhouse_exterior.jpg)
*Complete greenhouse prototype showing wooden frame and tarpaulin covering*

![Internal Layout](docs/greenhouse_interior.jpg)
*Internal structure showing soil beds, water tanks, and irrigation system*

The greenhouse structure features:
* Sturdy wooden frame resistant to water damage and environmental stress
* Tarpaulin covering (easily raised for access and maintenance)
* Demarcated internal sections: soil beds and water storage area
* Two water tanks: standard irrigation water and pH-treated water
* Roof-mounted drip irrigation piping system
* Sensor placement: soil probes in growing beds, atmospheric sensors on frame pillars
* Circuit box mounted on top with external LCD visibility
* Strategic component placement for power distribution and cable management

### Control Interface

![User Interface](docs/control_panel.jpg)
*Dual-LCD interface with keypad for parameter configuration and monitoring*

**Interface Features:**
* **LCD1 Display**: Shows live sensor readings (temperature, humidity, soil moisture, pH, UV index) updated in real-time
* **LCD2 Display**: Shows user-entered threshold values and current actuator status (pump ON/OFF, fan status, UV lamp state)
* **4×4 Keypad**: Allows input of crop-specific parameters without external devices
* **Offline Operation**: All configuration, monitoring, and control happens locally
* **Simple Configuration**: Enter minimum/maximum acceptable values for each parameter
* **Immediate Feedback**: System responds instantly to parameter violations
* **Accessible Design**: No technical expertise required for basic operation

## 4. Features

### Environmental Monitoring

* **Multi-parameter sensing**: Soil moisture, soil pH, soil temperature, atmospheric temperature, atmospheric humidity, UV light intensity, irrigation water pH
* **Real-time data acquisition**: Continuous monitoring with sub-second response times
* **Accurate measurements**: Calibrated sensors with ±5% accuracy for moisture, ±0.1 pH units, ±0.5°C temperature
* **Live display**: Instant feedback on LCD1 without external devices
* **Data transmission**: Reliable UART serial communication at 9600 baud

### Automated Control

* **Intelligent irrigation**: Activates pumps when soil moisture drops below threshold
* **Temperature regulation**: Fan control maintains optimal atmospheric temperature
* **Humidity management**: Coordinated fan operation prevents excessive moisture
* **Light supplementation**: UV lamp activates when natural light is insufficient
* **Water quality control**: Monitors irrigation water pH to prevent soil chemistry imbalances
* **Hysteresis logic**: Prevents rapid on-off cycling of actuators
* **Relay isolation**: Protects microcontrollers from high-current devices

### User Configuration

* **Crop-specific parameters**: Configure unique thresholds for different plant species
* **Growth stage adaptation**: Adjust parameters as crops progress through growth cycles
* **Simple keypad entry**: No smartphone or computer required
* **Threshold storage**: Values retained in memory for continuous operation
* **Dual-display feedback**: Simultaneous viewing of live data and configured targets
* **On-site operation**: All configuration happens directly at the greenhouse

### Power System

* **Dual-battery architecture**: Separate power rails for control and actuators
* **Voltage regulation**: Multiple LM2596 converters ensure stable 5V and 12V outputs
* **Backup runtime**: 4-5 hours continuous operation on battery power
* **Noise isolation**: Actuator switching doesn't interfere with sensor readings
* **Thermal protection**: Voltage regulators include overcurrent and thermal shutdown
* **Rechargeable batteries**: 12V 7Ah SLA batteries with standard charging interface

### Mechanical Design

* **Durable construction**: Wooden frame with water-resistant tarpaulin covering
* **Accessibility**: Easily opened for maintenance and crop access
* **Organized layout**: Clearly demarcated soil and water storage sections
* **Drip irrigation**: Roof-mounted pipes for uniform water distribution
* **Weather protection**: Circuit box shields electronics from moisture and dust
* **Sensor placement**: Strategic positioning for accurate environmental monitoring

## 5. How It Works

### System Architecture

```
Power System:
  Battery 1 (12V 7Ah) → LM2596 Regulators → 5V Control Rail
      ↓                                          ↓
  Battery 2 (12V 7Ah)                    Arduino MCU1 (Sensors)
      ↓                                          ↓
  LM2596 Regulators → 12V Actuator Rail    Serial TX/RX
      ↓                                          ↓
  Relays → Pumps, Fan, UV Lamp          Arduino MCU2 (Control)
                                                 ↓
                                    Keypad, LCD2, Relay Drivers
```

### Data Flow

**Sensing Loop (MCU1):**
1. Read all sensor values (analog and digital)
2. Convert raw readings to engineering units (%, pH, °C, %RH, UV index)
3. Display current values on LCD1
4. Package data as comma-separated serial packet
5. Transmit to MCU2 via UART (TX→RX)
6. Repeat continuously

**Control Loop (MCU2):**
1. Receive sensor data packet from MCU1
2. Parse values for each environmental parameter
3. Compare against user-configured thresholds
4. Implement control decisions:
   - Soil moisture < minimum → Activate irrigation pump
   - Temperature > maximum → Activate cooling fan
   - UV index < minimum → Activate UV supplemental lighting
   - pH outside range → Alert (water change required)
5. Update actuator states via relay drivers
6. Display status and thresholds on LCD2
7. Repeat continuously

### Control Logic

The system implements feedback control with hysteresis to prevent rapid switching:

**Irrigation Control:**
* Pump ON when: Soil moisture < (Threshold - Hysteresis)
* Pump OFF when: Soil moisture > (Threshold + Hysteresis)
* Typical hysteresis: ±5% moisture

**Temperature Control:**
* Fan ON when: Temperature > Maximum threshold
* Fan OFF when: Temperature < (Maximum - Hysteresis)
* Default operation: Fan remains ON to maintain equilibrium

**UV Light Control:**
* UV lamp ON when: UV index < Minimum threshold
* UV lamp OFF when: UV index > (Minimum + Hysteresis)
* Supplements natural sunlight during low-light periods

### User Interaction

**Initial Configuration:**
1. Power on system (both batteries connected)
2. LCD2 prompts for threshold entry via keypad
3. Enter minimum/maximum values for:
   - Soil moisture (%)
   - Temperature (°C)
   - Humidity (%RH)
   - UV index
   - Soil pH
   - Water pH
4. System stores values and begins automated control
5. Thresholds can be updated anytime via keypad

**Ongoing Operation:**
1. LCD1 continuously shows live sensor readings
2. LCD2 shows thresholds and actuator status
3. System automatically maintains conditions
4. User can observe system behavior without intervention
5. Manual override not required during normal operation

### Communication Protocol

**Serial Data Format (MCU1 → MCU2):**
```
"moisture,soil_pH,soil_temp,air_temp,humidity,UV,water_pH\n"
Example: "45.2,6.8,25.3,26.1,65.0,1.2,7.0\n"
```

**Parsing and Validation:**
* MCU2 splits packet on commas
* Validates each value is within sensor range
* Rejects malformed packets (keeps last good values)
* Prevents control decisions based on corrupted data

## 6. Results and Performance

### Power Supply Validation

All components received stable regulated voltages within acceptable tolerances:

| Component | Required Voltage | Measured Voltage | Error |
|-----------|-----------------|------------------|-------|
| Soil Moisture Sensor | 5.0V | 4.98V | 0.4% |
| DHT22 Sensor | 5.0V | 5.01V | 0.2% |
| UV Sensor | 5.0V | 4.95V | 1.0% |
| LCD Displays | 5.0V | 5.00V | 0.0% |
| Relay Modules | 5.0V | 4.97V | 0.6% |

### Sensor Performance

**Soil Moisture Control:**

| Soil Condition | Measured Level | System Response |
|---------------|---------------|----------------|
| Dry soil | 13% | Irrigation activated → pump ON |
| Slightly moist | 28% | Irrigation activated → pump ON |
| Adequate moisture | 62% | No action → pump remains OFF |
| Saturated soil | 88% | No action → excess recognized |

The capacitive soil moisture sensor demonstrated excellent sensitivity across the full moisture range, reliably triggering irrigation when levels dropped below 30% and stopping when adequate moisture (30-70%) was restored.

**Temperature and Humidity Control:**

| Environmental Condition | Sensor Reading | System Response |
|------------------------|---------------|----------------|
| Minimum temperature | 22.8°C | Fan ON to maintain equilibrium |
| Normal range | 22.8-26.0°C | Fan ON (default operation) |
| Warmer condition | ≥26.0°C | Fan ON continuously |
| Colder condition | ≤22.7°C | Fan OFF to prevent overcooling |

The DHT22 sensor maintained accurate readings with ±0.5°C precision. The control logic successfully prevented overheating while avoiding unnecessary cooling during cold periods.

**UV Light Monitoring:**

| Light Condition | UV Index | System Response |
|----------------|----------|----------------|
| No light | 0.1 | Below threshold (supplemental lighting may activate) |
| Low light | 0.3 | Insufficient for optimal growth |
| Adequate light | 1.0 | No supplemental lighting needed |
| Added sunlight | 1.4 | Natural light sufficient |

The UV sensor provided proportional readings corresponding to light intensity, enabling intelligent control of supplemental lighting to maintain optimal photosynthetically active radiation.

**Water Quality Monitoring:**

| Water Type | Measured pH | Assessment |
|-----------|------------|-----------|
| Normal tap water | 7.0 | Neutral - acceptable |
| Saline water | 7.5 | Slightly basic - acceptable |
| Acidic water | 5.2 | Too acidic - water change needed |
| Alkaline water | 8.9 | Too basic - water change needed |

The liquid pH sensor accurately detected water chemistry variations, alerting when irrigation water pH fell outside the safe range (6.0-8.0) for most crops.

### System Integration Performance

**Communication Reliability:**
* Serial data transmission: 100% success rate at 9600 baud
* No data corruption observed during extended testing
* Packet parsing: Robust handling of complete and incomplete packets

**Response Time:**
* Sensor reading to LCD display: <1 second
* Threshold violation to actuator activation: <2 seconds
* User keypad input to system acknowledgment: Immediate

**Operational Stability:**
* Continuous runtime test: 5+ hours without failures
* No microcontroller resets or communication dropouts
* Voltage regulation remained stable throughout discharge cycle
* No electrical interference between control and actuator subsystems

### Practical Insights

**What Worked Exceptionally Well:**
* Dual-microcontroller architecture provided clean separation of concerns
* Separate battery rails eliminated actuator noise interference with sensors
* Capacitive soil moisture sensor proved durable and corrosion-resistant
* DHT22 delivered reliable atmospheric monitoring in greenhouse humidity
* Relay isolation protected microcontrollers while switching high-current loads
* Keypad + dual-LCD interface made the system accessible to non-technical users
* Offline operation eliminated dependence on internet connectivity

**Key Challenges and Solutions:**
* **Initial Challenge**: Soil sensor accuracy varied with soil composition
  - **Solution**: Calibration procedure using gravimetric moisture measurement
  
* **Initial Challenge**: pH sensors required frequent calibration
  - **Solution**: Standard buffer solution calibration protocol (pH 4, 7, 10)
  
* **Initial Challenge**: Relay switching caused voltage transients
  - **Solution**: Flyback diodes (1N4007) across all relay coils
  
* **Initial Challenge**: Managing power budget across multiple actuators
  - **Solution**: Dual-battery architecture with dedicated actuator power rail

**African Context Considerations:**
* System operates reliably in tropical temperatures (25-35°C)
* No internet requirement makes it suitable for rural deployment
* All components available in Nigerian electronics markets (Lagos, Benin City)
* Repair and maintenance possible with local technical skills
* Cost-effective compared to non-existent commercial alternatives

## 7. Technologies Used

**Hardware:**
* Arduino Uno microcontrollers (3x ATmega328P)
* Capacitive soil moisture sensor
* Soil pH sensor (analog probe)
* Liquid pH sensor (pH-4502C with E201-BNC electrode)
* DHT22 temperature and humidity sensor
* SENS43UV ultraviolet sensor
* 16×2 LCD displays with I²C interface (2x)
* 4×4 matrix keypad
* One-channel relay modules (5x)
* LM2596 DC-DC buck converters (6x)
* 12V 7Ah SLA batteries (2x)
* 5V DC water pumps (2x)
* 12V DC cooling fan
* 12V UV LED strip (120 LEDs, 395-405 nm)
* NEMA 17 stepper motor with A4988 driver
* 1N4007 flyback diodes (5x)
* NPN transistors for relay drivers
* Resistors (1kΩ, 2kΩ, 3.1kΩ, 4.7kΩ)
* Connector wires and jumper wires

**Firmware:**
* Arduino IDE (C/C++ embedded programming)
* Non-blocking millis()-based timing architecture
* UART serial communication (9600 baud)
* I²C protocol for LCD communication
* DHT22 library for digital sensor interfacing
* Keypad library for matrix scanning
* LiquidCrystal_I2C library for display control

**Control Algorithms:**
* Feedback control with hysteresis
* Threshold-based decision logic
* Serial data packet parsing and validation
* Multi-sensor data fusion
* Automated actuation based on environmental conditions

**Design and Development Tools:**
* Circuit design and simulation
* SolidWorks CAD (mechanical greenhouse design)
* Multimeter testing and calibration
* Pandoc (documentation conversion)
* Standard buffer solutions (pH calibration)

## 8. Future Improvements

### High Priority Enhancements

* **Solar power integration** with MPPT charge controller for off-grid sustainability
* **Data logging system** using SD card module for historical analysis
* **Improved pH control** with automated acid/base dosing pumps
* **Soil nutrient monitoring** (NPK sensors) for comprehensive fertility management
* **Advanced sensors**: CO₂ concentration, light spectrum analysis
* **Backup communication**: LoRa for remote monitoring in areas without cellular coverage

### System Optimization

* **Predictive control algorithms**: Use historical data to anticipate irrigation needs
* **Machine learning integration**: Optimize thresholds based on crop performance
* **Multi-zone control**: Independent parameter management for different crop sections
* **Enhanced power management**: Deep sleep modes during inactive periods
* **Improved calibration**: Self-calibration routines for long-term sensor accuracy
* **Weatherproofing upgrades**: Sealed sensor housings for outdoor deployment

### Scalability and Integration

* **Modular expansion**: Support for additional sensor types without firmware rewrite
* **Cloud connectivity** (optional): IoT platform integration for remote monitoring
* **Mobile application**: Bluetooth interface for smartphone-based configuration
* **Automated pest detection**: Camera-based vision system for disease monitoring
* **Integration with weather forecasting**: Adjust irrigation based on rain predictions
* **Multiple greenhouse management**: Central control system for farm-scale deployment

### Educational and Research Extensions

* **Curriculum development**: Educational modules for agricultural training
* **Open-source platform**: Release complete design files and code for community development
* **Research partnerships**: Collaboration with agricultural universities for field trials
* **Crop-specific profiles**: Pre-configured parameter sets for common Nigerian crops (tomatoes, peppers, lettuce, etc.)

## 9. Environmental Impact and African Context

This project demonstrates significant environmental, economic, educational, and social benefits within the African agricultural landscape:

### Sustainability Benefits

* **Water conservation**: Automated irrigation reduces water waste by 30-50% compared to manual methods
* **Energy efficiency**: Targeted actuator control minimizes unnecessary electricity consumption
* **Resource optimization**: Precise environmental control reduces fertilizer and pesticide needs
* **Extended growing seasons**: Controlled environment enables year-round crop production
* **Reduced chemical use**: Optimal growing conditions improve plant health and disease resistance
* **Promotes local food production**: Reduces dependence on imported produce

### Economic Impact

* **Affordable precision agriculture**: ~₦450,000 (~$300 USD) vs. non-existent commercial alternatives
* **No commercial options available**: This technology is completely absent from African markets
* **Accessible components**: All parts available in Nigerian electronics markets (Computer Village Lagos, Benin City)
* **Eliminates internet dependency**: No monthly connectivity costs or reliance on unstable infrastructure
* **Local maintenance**: Repairable using locally available technical skills and replacement parts
* **Reduced foreign exchange burden**: No need to import expensive commercial systems
* **Increased crop yields**: Optimized conditions can double or triple production compared to traditional methods
* **Income generation**: Enables small-scale farmers to grow high-value crops year-round

### Educational and Research Value

* **Hands-on engineering training**: Demonstrates integration of sensors, microcontrollers, and actuators
* **Practical agricultural technology**: Bridges gap between classroom theory and field application
* **Research platform**: Supports agricultural experiments in controlled conditions
* **Skills development**: Builds capacity in embedded systems, automation, and precision agriculture
* **Open educational resource**: Complete documentation enables replication by students and researchers
* **Interdisciplinary learning**: Combines electrical engineering, agriculture, environmental science

### Social and Community Benefits

* **Food security**: Improves local food production capacity in urban and peri-urban areas
* **Youth engagement**: Attracts young people to modern agriculture through technology
* **Women empowerment**: Reduces physical labor, making greenhouse farming more accessible to women
* **Urban agriculture**: Enables controlled-environment food production in cities
* **Climate resilience**: Provides adaptation strategy for unpredictable weather patterns
* **Knowledge sharing**: Creates opportunities for farmer-to-farmer technology transfer

### African Context Advantages

* **Tropical climate suitability**: Tested under Nigerian environmental conditions (25-35°C)
* **Rural accessibility**: Offline operation works in areas without internet or cellular service
* **Local supply chain**: No dependence on international shipping or imports
* **Appropriate technology**: Designed for local conditions, not adapted from Western systems
* **Maintenance accessibility**: Uses standard electronics components with local availability
* **Cultural appropriateness**: Simple interface accessible to farmers with varying literacy levels
* **Scalability**: Design can be adapted from household to commercial farm scales

### Long-term Development Impact

* **Technology transfer**: Demonstrates how global agricultural technology can be localized
* **Entrepreneurship opportunities**: Creates potential for local greenhouse system manufacturing
* **Agricultural innovation**: Establishes foundation for further precision agriculture development
* **Policy influence**: Provides evidence for government investment in agricultural technology
* **Regional adaptation**: Design can be replicated across Sub-Saharan Africa with minor modifications

## 10. Authors

**Blessed Ariagbofo** (Primary Author)  
Department of Electrical and Electronic Engineering  
University of Benin, Benin City, Edo State, Nigeria  
Email: blessedariagbofo@gmail.com

**Omorogiuwa Rejoice Etinosa** (Second Author)  
Department of Electrical and Electronic Engineering  
Edo State University, Iyamho, Edo State, Nigeria

## 11. License

Open-source for educational and research use.  
Commercial use requires permission.

---

**This project demonstrates that affordable precision agriculture technology can be developed locally in Africa, addressing food security challenges while building technical capacity and promoting sustainable farming practices.**
