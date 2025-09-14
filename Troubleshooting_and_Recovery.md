# Troubleshooting and Recovery

## Quick Reference Guide

This document provides  troubleshooting steps, diagnostic procedures, and recovery protocols for the Scattered Gazes installation. For detailed operational procedures, see the [Gallery Playbook](Gallery_Playbook_ScatteredGazesAIBias.md).

## Common Issues & Immediate Solutions

### Display Problems
- **Screen Frozen/Unresponsive:**
  - Press Arduino reset button (small button on board)
  - Wait 10 seconds for system reboot
  - If persistent: Check power connections, contact technical support

- **LED Matrix Issues:**
  - **No LEDs lighting:** Check 5V power supply, verify WS2812B strip connections
  - **Wrong colours/patterns:** Restart system, check for loose data connections
  - **Flickering/dim LEDs:** Check power supply capacity (minimum 3A required)
  - **Individual LED failures:** Document location, continue operation if <5 LEDs affected

### Audio Problems
- **No Sound:** 
  - Check volume control, verify MP3 files on SD card
  - Look for DFPlayer LED indicators (slow blink = normal)
  - Test with headphones to isolate speaker issues

- **Audio Distorted:**
  - Check power supply stability
  - Verify file format (MP3, 44.1kHz recommended)
  - Reduce volume if overdriving speaker

### Mechanical Issues
- **Servo Motor Problems:**
  - Grinding noise: Immediate emergency stop, check for obstructions
  - Erratic movement: Verify power connections, check position feedback
  - Overheating: Allow cooling time, check for mechanical binding

### Interaction Problems
- **Touch Interface Lag:**
  - Clean screen with microfibre cloth
  - Check for electromagnetic interference
  - Restart system if delay >2 seconds

## Diagnostic LED Matrix

### Arduino Status LEDs
| LED State | Meaning | Action Required |
|-----------|---------|-----------------|
| Solid Green | Normal operation | None |
| Blinking Blue | System initialising | Wait 30 seconds |
| Blinking Red | Error detected | Check LCD for error code |
| Solid Red | Emergency shutdown | Check temperature/power |

### Power Supply Indicators
| LED State | Meaning | Action Required |
|-----------|---------|-----------------|
| Solid Green | Normal 5V output | None |
| Dim Yellow | Voltage fluctuation | Check connections |
| Off | Power failure | Replace immediately |

### DFPlayer Audio Module
| LED State | Meaning | Action Required |
|-----------|---------|-----------------|
| Slow Blink | Files loading correctly | None |
| Fast Blink | Audio playing | None |
| Solid | File system error | Reformat SD card |
| Off | Module failure | Check connections |

## Recovery Protocols

### After Power Failure
1. Wait 30 seconds before reconnecting power
2. System automatically resumes at next cycle start
3. Run full system test via LCD interface
4. Document incident in maintenance log

### After Emergency Stop
1. Identify and clear cause of emergency stop
2. Press "RESET" on Arduino after issue resolved
3. Run complete diagnostic cycle
4. Verify all systems operational before public use
5. Log incident with timestamp and resolution

### After Software Crash
1. Arduino automatically reboots within 10 seconds
2. If repeated crashes occur, contact artist immediately
3. Use USB backup to restore to known good state
4. Document crash frequency and conditions

## System Restore Procedures

### Firmware Recovery
```bash
# Connect Arduino via USB
# Upload backup firmware from emergency kit:
# - scattered_gazes_main.ino
# - audio_controller.ino
# - servo_control.ino
# - led_effects.ino
# - touch_interface.ino
```

### SD Card Recovery
1. Format SD card as FAT32
2. Copy MP3 files from backup in numerical order (001.mp3 - 012.mp3)
3. Test audio playback before reinserting
4. Verify all audio cues function correctly

## Performance Monitoring

### System Health Checks
- **Daily:** Visual inspection, performance log entry
- **Weekly:** Component wear assessment, connection checks
- **Monthly:** Full system backup, calibration verification

### Warning Signs
- Temperature alerts on LCD display
- Servo motor noise or binding
- Irregular LED patterns
- Touch interface delays >1 second
- Audio dropouts or distortion

## Emergency Contacts

### Immediate Support
- **Artist/Developer:** [Contact Information]
- **Gallery Technical Staff:** [Local Contact]
- **Emergency Services:** 999 (fire/electrical hazards)

### Component Suppliers
- **Same-day London:** Pimoroni (Arduino, servos)
- **Local Nottingham:** Maplin Electronics (basic components)
- **24/7 Emergency:** RS Components (power supplies, critical parts)

## Documentation Links

- [Gallery Playbook](Gallery_Playbook_ScatteredGazesAIBias.md) - Complete operational procedures
- [Technical Architecture](Technical_Architecture.md) - System specifications and wiring
- [Suppliers & Components](Suppliers_Component_List.md) - Parts sourcing and contacts

***

*This document should be updated with any new issues discovered during operation. Report persistent problems to technical support for documentation and resolution.*

