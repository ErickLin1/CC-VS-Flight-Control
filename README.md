### This universal flight control is rewritten based on the previous generation of quadcopter propeller flight control.
### The principle of the previous generation of quadcopter flight control is to use cc to control the speed of the speed controller, modify the lift and anti-torque brought by the physical bearing propeller (flap bearing + flap), and then realize attitude closed-loop control.
### But because of this, deployment and parameter adjustment are very troublesome, and it is not easy to copy to other models, and the versatility is poor.

### So this version of universal flight control was born. It uses the extended API of cc:vs as the power source, which can be used out of the box and deployed with one click, which is very convenient. xxx
### The new version no longer relies on ccvs, but changes all power to void power (void power) mod,
### My goal is to make it simulate the operating feel of various types of aircraft, and have basic functions such as autopilot, path finding, obstacle avoidance, etc.

### The full function requires the installation of Kallen's MetaPhysics scanner API (follow mode, hms_fly mode, switch player name, etc.)
### https://github.com/KallenKas024/Metaphysics/

> Special thanks:
@kallen provided metaphysics mod: The radar scanner and ray detection (block scanner) of the flight control use the API provided by this mod
Thanks to @kallen for adding mod functions according to my needs

## newVersion is the new version, which reconstructs the core part, relies on void power mod, and supports void power holographic screen
> Added holographic display GUI (void power), power changed from ccvs to void power's void engine
> Deployment requires an engine controller peripheral (only 1 can be placed), and a void engine (any number, no need to be a peripheral, just put it on the ship)
### https://github.com/dfdyz/VoidPowerMod

>
### Update log:
* 2024/4/05 Added quadRotor mode: attitude mode, fixed point mode
* 2024/4/10 Added follow mode (follow): follow the player -- the player scanner API comes from @kallen's metaphysics mod
* 2024/4/20 Added point loop mode (pointLoop): Circulate between target points (no obstacle avoidance)
* 2024/5/25 Added spaceShip mode (spaceShip): manual mode (angular velocity closed loop + speed closed loop), fixed point mode (angle closed loop + position closed loop)
* 2024/5/29 Added quad_FPV mode: (angular velocity closed loop)
* 2024/5/31 Added space-based cannon mode (hms): fire lasers from the player's line of sight, set the block as the target when detected, and aim the aircraft head at the target block -- the scanner API comes from @kallen's metaphysics mod
* 2024/6/01 Added mouse flight mode (hms): same as space-based cannon mode, but with controller direct drive
* 2024/6/02 Added wind resistance and gravity enhancement (quad_FPV): added air resistance simulation and gravity simulation to the cross-country mode (enhanced on the basis of Valkyrie's own gravity) -- suggestion from @FEMO114
* 2024/6/04 Added cross-country mode: assisted hovering mode (angle closed loop + speed closed loop)
* 2024/6/05 Added parameter adjustment system and made the first version of the GUI interface
* 2024/6/06 Added lock mode button-can switch lock in gui
* 2024/6/08 Added helicopter mode
* 2024/6/09 Added independent parameter adjustment interface for helicopter mode: various parameters of helicopter mode can be set separately to simulate the feel of different types of helicopters
* 2024/6/12 Added multi-monitor support: Added interface manager, which can connect multiple monitors at the same time to operate the flight control together -- proposed and implemented by @siiftun1857 (contributed code) by @siiftun1857
* 2024/6/19 Added physical frame mode: Different from the previous mode, this mode captures the physical frame as the flight control operating frequency. (If not captured, enable game tick mode for 0.05s)
* 2024/6/21 Add full-angle physicalization support: Now vehicles facing any direction can modify the initial orientation through the set_att interface to obtain the correct attitude solution and control
* 2024/6/23 Add multi-window instances: Now support displays of any size and allocate multi-window copies
* 2024/6/24 Completely rewrite the interface: Use the ATT interface as the main interface, and add window merging functions, quick parameter adjustment, controller input status display, etc., and add color theme modification page
* 2024/6/25 Add afterburner mode (spaceShip): Afterburner mode increases the force output by the spacecraft - the ratio can be modified on the parameter adjustment page -- suggestion from @我不是冰淇淋-_-
* 2024/6/26 Add airship mode (airShip): Angle closed loop (PITCH, ROLL) = 0, you can operate yaw, front and back, left and right, up and down, etc. Similar to a rudder, but can be moved left and right.
* 2024/6/27 Added independent parameter adjustment interface to airship mode
* 2024/7/05 Added camera mode: Request connection to the target spaceship, and turn on camera mode after agreeing - can rotate around the target spaceship and follow it
* 2024/7/06 Adjustment of starship mode: independent hovering force. Now the force of the upper and lower nozzles is available (follows the rotation)
* 2024/7/08 Update of starship mode: decoupling mode
* 2024/7/20 Added Rate (stick curve, throttle curve) to cross-country mode, same as BetaFlight. In reality, all the rates based on BetaFlight flight control can be restored
* 2024/11/1 Added Void Power version flight control
* 2024/11/7 Added holographic screen GUI (Void Power)
* 2024/11/15 Added holographic screen fire control lock interface
* 2024/11/16 Added built-in fire control radar for flight control
* 2024/11/24 Added ammunition display, radar target name, and health display
* 2024/12/01 Added spacecraft network whitelist function
* 2024/12/17 Added automatic balancing/cruise control function (starship mode)
* 2024/12/21 Added recording and playback functions
* 2024/12/22 Added disconnection reconnection (automatically connect to the last connected parent when powered on)
