# New_BFA
#include <kipr/botball.h>
#include <ARM.h>
int main()
{
    
    
    void thread_function()
    {
        set_servo_slow(claw,claw_for_dump+100);
        msleep(300);
        set_servo_slow(claw,claw_for_dump);
        msleep(300);
    }
    thread moveanddrop;
    moveanddrop = thread_create(thread_function);
    create_connect();
    create_full();
    
  set_servo_slow(shoulder,shoulder_start_position);
   set_servo_slow(wrist, 322);
  set_servo_slow(claw, claw_closed);

    create_drive_direct(-200, -200);
    msleep(500);
    create_stop();
    msleep(3000);//take this out after wait for light is functional
    //wait_for_light(0);
    create_drive_direct(100,100);//set up palms
    msleep(400);
    create_stop();
    move_claw(claw_open);
    move_wrist_to(wrist_for_front_pickup);
    msleep(300);
    shoulder_doze();//don't touch above
    create_drive_direct(60, 60);
    msleep(900);
    claw_slow_close();
    create_stop();
    create_drive_direct(-300,-300);
    msleep(700);
    move_claw (claw_open);
    create_forward(1400);//perfect
    claw_slow_close();
    create_backward(1500);//backs up into wall for first half of squareup
    create_forward(600);//moves away from wall for second half of squareup
    create_drive_direct(-200, 200);//turning for second half of squareup
    msleep(800);
    create_stop();
    doze_to_dump();//move arm from doze to dump
    create_drive_direct(50, 100);
    msleep(1000);//good but not 
    create_stop();
    create_backward(1200);//perform second half of squareup
    //at this point, Create is squared up in starting box, facing tram, with poms in dump position bucket
    create_forward(4175);//experimental travel numbers to get claw to tram...change and add to this to get in position to make the next CCW turn
    CW(85);
    set_servo_slow(wrist,110);
    thread_start(moveanddrop);
    create_forward(750);//create_forward(4750);//commented out 
    thread_destroy(moveanddrop);
    msleep(500);
    
    //FROM ABOVE IS GOOD
    CCW(85);
    create_backward(5000);
    create_forward(600);
    create_drive_direct(200, -200);//turning for second half of squareup
    msleep(800);
    create_stop();
    create_backward(1500);
    
    
    //above is squared
                       
                       //f r i s b e e c o d e 
    set_servo_slow(wrist, sandwich_approach_wrist);
    set_servo_slow(shoulder,sandwich_approach_shoulder);
    set_servo_slow(claw, sandwich_approach_claw);
    
    create_drive_direct(0,100); // right arc 
    msleep(1800);
    create_stop();
    
    create_drive_direct(190,90);//arc toward tree
    msleep(3400);
    create_stop();
    
    create_forward(200); // forward to tree
    
    create_drive_direct(0,100);
    msleep(450); // right arc to tree
    create_stop();
    
    create_forward(120);
    
    create_drive_direct(-50,100);// slight movement to correct
    msleep(100);
    create_stop();
    msleep(250);
    set_servo_slow(claw,sandwich_adjust_claw);
    set_servo_slow(shoulder,sandwich_adjust_shoulder);
    doze_to_dump2(); // raises before backup
        
    set_servo_slow(claw, 1800);
    create_drive_direct(50,-100);
    msleep(100);
    create_stop(); // reversal of getting there
    create_backward(120);
    create_drive_direct(0,-100);
    msleep(450);
    create_stop();
    create_backward(800);
    create_drive_direct(-190,-90);
    msleep(3400);
    create_stop();
    create_drive_direct(0,-100);
    msleep(2000);
    create_stop();
    create_backward(400);
    
    create_forward(600);//moves away from wall for second half of squareup
    create_drive_direct(-200, 200);//turning for second half of squareup
    msleep(800);
    create_stop();
    create_drive_direct(50, 100);
    msleep(1000);//good but not 
    create_stop();
    create_backward(1600);//perform second half of squareup
    //at this point, Create is squared up in starting box, facing tram, with poms in dump position bucket
    create_forward(4175);//experimental travel numbers to get claw to tram...change and add to this to get in position to make the next CCW turn
    CW(85);
    set_servo_slow(wrist,110);
    thread_start(moveanddrop);
    create_forward(450);
    thread_destroy(moveanddrop);
    msleep(500);
    
    create_backward(500);//backup from tram to adjust arm
    set_servo_slow(claw,claw_open_for_cubes);
    set_servo_slow(shoulder, shoulder_for_cubes); //grab positions
    set_servo_slow(wrist, wrist_for_cubes);
    create_forward(500);//go back to start position
    
    //place movement to square around middle of pvc bar
    msleep(5000);//this is to show where Create is before next line of code
    create_backward(600);//square into wall
    create_forward(2250);//go towards cubes
    set_servo_slow(claw, claw_closed_for_cubes);//grab cubes
    create_backward(400);//back out of area
    CCW(800);//turn to drop cubes
    create_forward(300);//new experiment____________________________________________________
    set_servo_slow(claw,claw_open);//drop cubes
   create_backward(300);//new experiment...second half
    CW(800);//turn back, while also knocking off top cube
    set_servo_slow(claw,claw_closed);//close claw to move in towards botguy
    set_servo_slow(wrist, wrist_pickup_botguy);//move to perfect spot to pick up botguy
    set_servo_slow(shoulder, shoulder_pickup_botguy);//move to perfect spot to pick up botguy
    create_forward(400);//go towards bot guy a little bit
    set_servo_slow(claw, claw_PVC_fill);//set claw to fill up the pvc area
    create_forward(200);//finish going to bot guy
    set_servo_slow(claw, claw_closed_for_cubes);//close around bot guy
    create_backward(800);//back out of box
    doze_to_dump3(); //raise up bot guy NOTE: should be  modified to be extremely slow (3rd version)
    create_backward(1000);//go backward to 180 to put bot guy down
    CW(2000); //180 turn to put bot guy in
    set_servo_slow(claw, claw_open);//drop off bot guy
    CW(1000);//90 degree
    create_backward(500); //back up to turn to square up
    CW(1000); // 90 degree
    create_backward(1100);
    //turn to put claw on tram
    msleep(0); //adjust time to coordinate with each robot
    // ??? ideas for the rest: close on bar and push all the way to the other side, note that it might change for each run considering in seeding bot guy will hopefully
	// be in the tram, whereas in other rounds, this may not quite be true.
    
    
    disable_servos();
    create_safe();
    create_disconnect();
    return 0;
}
