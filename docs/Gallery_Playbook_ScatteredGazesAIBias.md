# Scattered Gazes Technical Theatre Playbook

## Arduino-Controlled Interactive Installation - Gallery Operations Guide

*Professional technical documentation for exhibition staff, maintenance teams, and emergency troubleshooting.*

***

## Table of Contents

- [System Overview](#system-overview)
- [Quick Start Guide](#quick-start-guide)
- [Technical Specifications](#technical-specifications)
- [Troubleshooting Matrix](#troubleshooting-matrix)
- [Maintenance Schedule](#maintenance-schedule)
- [Emergency Procedures](#emergency-procedures)
- [Replacement Parts & Suppliers](#replacement-parts--suppliers)
- [Software Backup & Recovery](#software-backup--recovery)
- [Exhibition-Specific Settings](#exhibition-specific-settings)
- [Safety Certifications & Compliance](#safety-certifications--compliance)
- [Post-Exhibition Procedures](#post-exhibition-procedures)
- [Emergency Contacts](#emergency-contacts)

***

## System Overview

### Installation Components

- **Primary Structure**: Champagne wooden crate (50cm × 33cm × 18cm)
- **Secondary Structure**: 
- **Control System**: Arduino Uno Rev3 with custom firmware
- **Scene Automation**: Dual SG90 servo motors for backdrop transitions
- **User Interface**: " resistive touch LCD display
- **Lighting**: WS2812B addressable LED strips (60 LEDs total)
- **Audio**: DFPlayer Mini MP3 module with 8Ω 3W speaker
- **Power**: 5V 3A switching power supply with backup battery
- **Safety**: Temperature monitoring and automatic shutdown systems

### Performance Specifications

- **Cycle Duration**: 5 minutes per complete experience
- **Daily Capacity**: ~288 complete cycles (24/7 operation)
- **User Decision Window**: 45 seconds with countdown timer
- **Scene Transition Time**: 3 seconds per backdrop change
- **Audio Segments**: 30 seconds maximum per scene
- **Interaction Response**: <500ms touch recognition

***

## Quick Start Guide

*For Daily Operation*

### Morning Startup Checklist (5 minutes)

**Step 1: Visual Inspection**
- [ ] Crate exterior undamaged, viewing window clean
- [ ] All LED eyes visible and undamaged
- [ ] Central figure properly positioned
- [ ] Touch screen clean and responsive
- [ ] No loose wires or components visible

**Step 2: System Power-Up**
- [ ] Connect main power supply (green LED indicator should illuminate)
- [ ] Arduino boots automatically (blue LED blinks 3 times)
- [ ] Touch screen displays "SCATTERED GAZES - READY"
- [ ] Audio test: Brief welcome message plays
- [ ] LED test: All eyes pulse once in sequence

**Step 3: Automated Systems Check**
- [ ] Touch "SYSTEM TEST" on LCD display
- [ ] Servo Test: Both motors cycle through all 4 positions
- [ ] Audio Test: 5-second sample from each scene plays
- [ ] LED Test: All strips cycle through red/green/blue
- [ ] Display shows "ALL SYSTEMS OPERATIONAL" or error codes

**Step 4: Baseline Performance**
- [ ] Run one complete 5-minute cycle
- [ ] Verify both Path A and Path B function correctly
- [ ] Check audience interaction responsiveness
- [ ] Document any issues in operations log

### Evening Shutdown (Optional - System designed for 24/7)

**Step 1: Graceful Shutdown**
- [ ] Touch "MAINTENANCE MODE" during scene transitions
- [ ] Allow current cycle to complete naturally
- [ ] System displays "SAFE TO POWER DOWN"

**Step 2: Secure Installation**
- [ ] Lock access panel if required by venue
- [ ] Ensure viewing window is clean
- [ ] Check surrounding area for debris
- [ ] Document daily performance in log

***

## Technical Specifications

### Arduino Programming Structure

```cpp
// CORE SYSTEM VARIABLES
int currentScene = 0; // 0-3 (4 scenes total)
int selectedPath = 0; // 0=undecided, 1=automated, 2=guided
unsigned long cycleStartTime; // 5-minute timer
boolean emergencyMode = false; // Safety override
```

**Main Programme Loop** *(Simplified Overview)*:
1. **Initialisation** (0:00-0:15): Welcome, system check, user role assignment
2. **Decision Point** (0:15-1:00): 45-second choice window with countdown
3. **Path Execution** (1:00-4:15): Automated scene progression based on selection
4. **Conclusion** (4:15-5:00): Comparative outcomes and call to action
5. **Reset** (5:00+): 30-second pause, return to initialisation

### Servo Motor Control

**Left Motor (Scene Selection)**:
- **Position 0**: Welcome/Introduction backdrop
- **Position 45°**: Colonial training materials
- **Position 90°**: Community consultation imagery
- **Position 135°**: Outcome displays

**Right Motor (Lighting/Effects)**:
- **Position 0**: Neutral positioning
- **Position 30°**: Triggers harsh corporate lighting
- **Position 60°**: Activates community celebration lighting
- **Position 90°**: Emergency reset position

**Motor Safety Limits**:
- Maximum rotation: 180° per motor
- Movement speed: 0.5 seconds per 45° increment
- Automatic position detection via potentiometer feedback? (may be cost prohibitive)
- Emergency stop if resistance exceeds threshold

### LED Lighting Programming

**WS2812B Strip Configuration**:
- **Strip 1** (20 LEDs): Top lighting for backdrop illumination
- **Strip 2** (20 LEDs): Side accent lighting for dramatic effect
- **Strip 3** (20 LEDs): Embedded in glass eyes for character response

**Lighting Scenes**:
```cpp
// PATH A: AUTOMATED AI (Colonial bias amplification)
goldenWarm(); // Seductive orientalist appeal (RGB: 255,215,0)
harshRed(); // Corporate surveillance (RGB: 220,20,60)
pulsingScarlet(); // Algorithmic objectification (RGB: 255,36,0)

// PATH B: HUMAN-GUIDED (Community collaboration)
coolAnalytical(); // Careful consideration (RGB: 70,130,180)
gentleBlue(); // Community voices (RGB: 100,149,237)
inclusiveWhite(); // Authentic recognition (RGB: 248,248,255)
```

### Audio System Configuration

**DFPlayer Mini Setup**:
- **Storage**: 32GB MicroSD card (FAT32 format)
- **File Structure**: Numbered MP3 files (001.mp3 through 012.mp3)
- **Quality**: 44.1kHz, 320kbps for exhibition-quality audio
- **Volume**: Automatically adjusts based on ambient sound sensor

**Audio Content Files**:
- **001.mp3**: Welcome narration (15 seconds)
- **002.mp3**: Choice presentation (30 seconds)
- **003.mp3**: Path A - Corporate efficiency voice (90 seconds total, 4 segments)
- **004.mp3**: Path B - Community collaboration voices (90 seconds total, 4 segments)
- **005.mp3**: Path A consequences (90 seconds)
- **006.mp3**: Path B outcomes (90 seconds)
- **007.mp3**: Final reflection and call to action (45 seconds)
- **008.mp3**: System error message (10 seconds)
- **009.mp3**: Maintenance mode notification (5 seconds)

***

## Troubleshooting Matrix

### Common Issues & Immediate Solutions

| Problem | Symptoms | Quick Fix | When to Call Artist |
|---------|----------|-----------|-------------------|
| **Screen Frozen** | Touch unresponsive, display static | Press reset button on Arduino | If reset doesn't restore function |
| **No Audio** | Visual working, no sound | Check volume knob, press audio test | If MP3 player LED not blinking |
| **Servo Jamming** | Grinding noise, backdrop stuck | Press emergency stop, manual reset | If motor feels hot or damaged |
| **LED Malfunction** | Eyes not lighting, wrong colors | Check power connections | If more than 5 LEDs non-functional |
| **System Won't Start** | Black screen, no response | Check main power cable | If Arduino power LED not illuminated |
| **Interaction Lag** | Delayed response to touch | Clean screen surface gently | If delay exceeds 2 seconds |
| **Wrong Scene Sequence** | Skips scenes or wrong order | Complete current cycle, then reset | If problem persists after reset |
| **Overheating Warning** | Temperature alert on screen | Ensure ventilation, reduce ambient heat | If alert continues after cooling |

### Diagnostic LED Indicators

**Arduino Onboard LED**:
- **Solid Green**: Normal operation
- **Blinking Blue**: System initialising
- **Blinking Red**: Error detected, check LCD for details
- **Solid Red**: Emergency shutdown active

**Power Supply LED**:
- **Solid Green**: Normal 5V output
- **Dim Yellow**: Voltage fluctuation (check connections)
- **Off**: Power supply failure (replace immediately)

**DFPlayer LED**:
- **Slow Blink**: MP3 files loading correctly
- **Fast Blink**: Audio playing normally
- **Solid**: File system error (reformat SD card)
- **Off**: Module failure or connection issue

***

## Maintenance Schedule

### Daily *(5 minutes, gallery staff)*
- [ ] Visual inspection of all components
- [ ] Screen cleaning with microfiber cloth
- [ ] Audio level check during quiet periods
- [ ] Performance log entry

### Weekly *(15 minutes, technical staff)*
- [ ] Servo motor lubrication (2 drops light machine oil)
- [ ] LED strip visual inspection for dead pixels
- [ ] Connection tightness check (gentle wiggle test)
- [ ] SD card backup verification
- [ ] Emergency procedures review with staff

### Monthly *(30 minutes, maintenance team)*
- [ ] Complete system backup to USB drive
- [ ] Component wear assessment (servos, LEDs, screen)
- [ ] Calibration check: servo positions and touch sensitivity
- [ ] Environmental sensor accuracy test
- [ ] Update operations log and order replacement parts

### Quarterly *(Artist consultation required)*
- [ ] Firmware update installation if available
- [ ] Performance optimisation based on usage data
- [ ] Community feedback integration review
- [ ] Educational content updates
- [ ] Long-term wear component replacement

***

## Emergency Procedures

### Immediate Shutdown *(When Required)*

**Fire/Water/Safety Emergency**:
1. **Unplug main power immediately** (red emergency button)
2. **Do not attempt component rescue** until area is secured
3. **Contact emergency services first**, artist second

**Electrical Problems**:
1. **Cut power at main supply** (switch behind installation)
2. **Do not touch exposed wires or smoking components**
3. **Evacuate 2-metre radius** until electrical safety confirmed

**Mechanical Failure**:
1. **Press emergency stop button** (yellow, top of control box)
2. **Allow current cycle to complete** if possible
3. **Note exact time and symptoms** for repair diagnosis

### System Recovery Procedures

**After Power Failure**:
- Wait 30 seconds before reconnecting power
- System automatically resumes at next cycle start
- Check all functions with system test mode

**After Emergency Stop**:
- Press "RESET" on Arduino after clearing mechanical issue
- Run complete diagnostic cycle before returning to public use
- Document incident in maintenance log

**After Software Crash**:
- Arduino automatically reboots within 10 seconds
- If repeated crashes, contact artist immediately
- USB backup can restore system to known good state

***

## Replacement Parts & Suppliers

### Critical Components *(Keep in Stock)*

**Arduino System**:
- Arduino Uno Rev3: £20 (Arduino.cc official)
- SG90 Servo Motors: £8/pair (Pimoroni, UK)
- " Touch LCD: 
- Power Supply 5V 3A: £15 (RS Components)

**Audio/Visual**:
- DFPlayer Mini: £8 (ModMyPi)
- WS2812B LED Strip: £25/metre (The Pi Hut)
- Speaker 8Ω 3W: £10 (Maplin Electronics)
- MicroSD Card 32GB: £12 (SanDisk Class 10)

**Mechanical**:
- Servo Horns/Gears: £5 (Complete set from Pimoroni)
- Mounting Hardware: £
- Backdrop Materials: £

**Suppliers**:
- **London**: Pimoroni 
- **Nottingham**: Maplin Electronics (Broadmarsh Centre)
- **National / online**: The Pi Hut
- **24/7 Emergency**: RS Components (Next-day guaranteed)

***

## Software Backup & Recovery

### System Restoration *(If Arduino Fails)*

**Required Files** *(USB Drive in Emergency Kit)*:
- `scattered_gazes_main.ino` - Primary Arduino sketch
- `audio_controller.ino` - MP3 player functions
- `servo_control.ino` - Motor positioning system
- `led_effects.ino` - Lighting control library
- `touch_interface.ino` - User interaction handling

**Upload Procedure**:
1. Connect Arduino to laptop via USB cable
2. Open Arduino IDE (installed on emergency laptop)
3. Load `scattered_gazes_main.ino`
4. Select "Arduino Uno" board, correct COM port
5. Upload sketch (takes 2-3 minutes)
6. Test all functions before returning to service

**SD Card Recovery**:
- Format SD card FAT32 on emergency laptop
- Copy MP3 files from USB backup in numerical order
- Test audio playback before reinserting

### Performance Data Collection

**Automated Logging** *(Arduino SD Card)*:
- Daily cycle counts and peak usage times
- User choice statistics (Path A vs Path B selection)
- Technical errors and system response times
- Environmental data (temperature, ambient light)

**Manual Logging** *(Gallery Staff)*:
- Audience engagement observations
- Interaction quality and comprehension
- Technical issues not caught by automated systems
- Maintenance performed and parts replaced

***

## Exhibition-Specific Settings

### Display Configuration

**Day Mode** *(6:00 AM - 6:00 PM)*:
- LED brightness: %
- Audio volume: % 
- Interaction timeout:  seconds (busy periods)
- Cycle frequency: Standard 5-minute complete cycles

**Evening Mode** *(6:00 PM - 10:00 PM)*:
- LED brightness: % maximum for dramatic effect
- Audio volume: % (quieter ambient environment)
- Interaction timeout:  seconds (more contemplative audience)
- Enhanced lighting effects for street visibility

**Night Mode** *(10:00 PM - 6:00 AM)*: (or switch-off completely)
- LED brightness: % (gentle presence, not disruptive)
- Audio volume: % (residential consideration)
- Automated cycles only (no interaction required)
- Gentle pulsing pattern to maintain interest

**Weather Adaptations**:
- **Rain**: Increased LED intensity to combat window reflections
- **Snow**: Slower scene transitions to account for cold weather effects on servos
- **Heat**: Automatic temperature monitoring with increased cooling pauses

***

## Safety Certifications & Compliance

### Electrical Safety
- **PAT Testing**: All components tested and certified for public use
- **Fire Rating**: Electronics enclosed in fire-resistant housing
- **IP Rating**: IP54 protection against dust and water spray
- **Emergency Shutdown**: Manual cutoff accessible to gallery staff

### Public Interaction Safety
- **Touch Surface**: Antimicrobial coating applied to LCD screen
- **Physical Barriers**: No exposed sharp edges or moving parts
- **Volume Limits**: Audio capped at 75dB maximum to prevent hearing damage
- **Child Safety**: All controls positioned above 1.2m height

### Data Protection
- **No Personal Data Collected**: System records only anonymous usage statistics
- **GDPR Compliance**: No cameras, microphones, or personal identification
- **Privacy**: No personal information required or recorded

***

## Post-Exhibition Procedures

### System Shutdown *(End of Exhibition)*
1. Complete final performance cycle gracefully
2. Export all performance data to USB drive
3. Photograph installation state for documentation
4. Power down in reverse startup sequence
5. Secure all components for transport

### Component Inventory *(For Artist Collection)*
- Document condition of all technical components
- Package servos and electronics in antistatic materials
- Preserve SD card with performance data
- Include complete maintenance logs and parts replacement history

### Educational Legacy Setup
- Upload performance data to GitHub repository
- Create final documentation with lessons learned
- Package replication guide for other venues
- Provide contact information for technical support

***

## Emergency Contacts

### Primary Support
**Artist/Developer**: 
- Mobile: Available daily during exhibition
- Email: Monitored every 2 hours during gallery operation
- Emergency: Text "SCATTERED GAZES URGENT" for priority response

### Technical Suppliers
**Arduino Support**: 
**Audio/Visual**: 
**Emergency Parts**: 

### Gallery Operations
**Arts Manager**: [contact]
**Exhibition Coordinator**: [project contact]

***

## Final Technical Notes

This installation represents the intersection of traditional paper theatre craft and contemporary AI ethics education. The Arduino automation serves both functional and metaphorical purposes - demonstrating human agency over algorithmic systems while providing reliable, accessible public engagement.

All technical choices prioritise:
- **Reliability** for 24/7 exhibition operation
- **Accessibility** for diverse audiences and technical skill levels
- **Safety** for public interaction in unsupervised environments
- **Educational Impact** supporting lasting behavioural change around AI ethics

**Complete technical documentation, including 3D printing files, circuit diagrams, and source code, will be available on GitHub following exhibition completion for educational replication.**

***

*This technical playbook ensures professional exhibition standards while supporting the work's educational mission of making AI ethics tangible and actionable for public audiences.*

**© 2025 - Technical Documentation Available Under Creative Commons**  
**GitHub Repository: [To be published post-exhibition]**
