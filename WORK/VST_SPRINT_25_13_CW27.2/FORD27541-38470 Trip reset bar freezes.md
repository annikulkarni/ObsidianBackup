what is app_screens.xml here we define each screen, and we will define actions that are handled in it by adding traps, each trap will have a target 
datums are defined in component.xml

- In app_screens.xml of iod we have this screen called iod_ok_trip_button_reseting_handler, this is the one which handles resetting animation, 
- in hal buttons component.xml we have defined all the actions of the button like, hold, press, released, hold_2 seconds etc.,
- now in this resetting there is no case for warning_active action, and what the screen should do when the warning is active,
- now i have added that and trying in target, working fine!!!, but but the screen is resetting but the action reset is not happening right now


Need confirmation on when
Resetting is complete, but the user has not yet released the ok button, and warning is triggered,  Whether the resetting action done, or resetting is cancelled
still waiting
made, resetting screen disapper by adding close screen trap in iod_ok_trip_button_reseting_handler
defect closed



