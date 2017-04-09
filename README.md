# GML-Controller-for-GUI
mousex = window_mouse_get_x();
mousey = window_mouse_get_y();
draw_set_halign(fa_center);
draw_set_valign(fa_center);
if obj_playerController.allyShipItems > 0
{
    if point_in_rectangle(mousex,mousey, 445, 325, 495, 375)
    {
        draw_set_alpha(1);
        if mouse_check_button_pressed(mb_left)
        {
        instance_create(obj_spaceship.x, obj_spaceship.y, Ally);
        obj_playerController.allyShipItems -= 1;
        }
    }
    else
    {
    draw_set_alpha(.8);
    }
}
else
{
    draw_set_alpha(.5);
}
draw_sprite(spr_makeally, -1, 470, 350);
if obj_playerController.techeng3
{
    if point_in_rectangle(mousex,mousey, 445, 390, 495, 440) && obj_spaceship.surgeCooldown = false
    {
        draw_set_alpha(1);
        if mouse_check_button_pressed(mb_left)
        {
            obj_spaceship.surgeCooldown = true;
            obj_spaceship.surge = true;
            obj_spaceship.alarm[6] = 200;
            obj_spaceship.alarm[7] = 1350;
        }
    }
    else
    {
    draw_set_alpha(.8);
    }
}
else
{
    draw_set_alpha(.5);
}
draw_sprite(spr_surge, -1, 470, 415);
if obj_playerController.techmil3
{
    if point_in_rectangle(mousex,mousey, 445, 455, 495, 505) && obj_spaceship.overloadCooldown = false
    {
        draw_set_alpha(1);
        if mouse_check_button_pressed(mb_left)
        {
            obj_spaceship.overloadCooldown = true;
            obj_spaceship.overload = true;
            obj_spaceship.alarm[6] = 200;
            obj_spaceship.alarm[8] = 1350;
        }
    }
    else
    {
    draw_set_alpha(.8);
    }
}
else
{
    draw_set_alpha(.5);
}
draw_sprite(spr_overload, -1, 470, 480);
if obj_spaceship.inStore == true
{
    draw_set_alpha(.7);
    draw_set_colour(c_green);
    draw_rectangle(100, 340, 400, 480, false);
    if point_in_rectangle(mousex,mousey, 119, 348, 221, 400)
    {
        draw_set_alpha(1);
        if mouse_check_button_pressed(mb_left) && obj_playerController.scrap >= 50
        {
            obj_playerController.scrap -= 50;
            obj_playerController.hullRepairs += 1;
            audio_play_sound(buttonpress, 1, 0);
        }
        else if obj_playerController.scrap < 50
        {
            draw_set_alpha(1);
            draw_set_colour(c_white);
            draw_text(250, 480, "Insufficient scrap!");
            draw_set_alpha(.7);
            draw_set_colour(c_green);
        }
        
    }
    else
    {
        draw_set_alpha(.7);
    }
    draw_sprite(spr_hullrepairitem, -1, 170, 374)
    if point_in_rectangle(mousex,mousey, 119, 408, 221, 460)
    {
        draw_set_alpha(1);
        if mouse_check_button_pressed(mb_left) && obj_playerController.scrap >= 50
        {
            obj_playerController.scrap -= 50;
            obj_playerController.homingMissiles += 1;
            audio_play_sound(buttonpress, 1, 0);
        }
        if obj_playerController.scrap < 50
        {
            draw_set_alpha(1);
            draw_set_colour(c_white);
            draw_text(250, 480, "Insufficient scrap!");
            draw_set_alpha(.7);
            draw_set_colour(c_green);
        }
    }
    else
    {
        draw_set_alpha(.7);
    }
    draw_sprite(spr_homingmissileitem, -1, 170, 434);
    if point_in_rectangle(mousex,mousey, 279, 348, 381, 400)
    {
        draw_set_alpha(1);
        if mouse_check_button_pressed(mb_left) && obj_playerController.scrap >= 25
        {
            obj_playerController.scrap -= 25;
            obj_playerController.allyShipItems += 1;
            audio_play_sound(buttonpress, 1, 0);
        }
        if obj_playerController.scrap < 25
        {
            draw_set_alpha(1);
            draw_set_colour(c_white);
            draw_text(250, 480, "Insufficient scrap!");
            draw_set_alpha(.7);
            draw_set_colour(c_green);
        }
    }
    else
    {
        draw_set_alpha(.7);
    }
    draw_sprite(spr_allyshipitem, -1, 330, 374)
    if point_in_rectangle(mousex,mousey, 279, 408, 381, 460)
    {
        if obj_spaceship.laserUpgrade == false
        {
        draw_set_alpha(1);
        }
        if mouse_check_button_pressed(mb_left) && obj_playerController.scrap >= 200 
        && obj_spaceship.laserUpgrade == false
        {
            obj_playerController.scrap -= 200;
            obj_spaceship.laserUpgrade = true;
            audio_play_sound(buttonpress, 1, 0);
        }
        if obj_playerController.scrap < 200
        {
            draw_set_alpha(1);
            draw_set_colour(c_white);
            draw_text(250, 480, "Insufficient scrap!");
            draw_set_alpha(.7);
            draw_set_colour(c_green);
        }
    }
    else
    {
        draw_set_alpha(.7);
    }
    draw_sprite(spr_laseritem, -1, 330, 434)
}
draw_set_alpha(.5);
draw_set_colour(c_green);
draw_rectangle(0, 500, 500, 625, false);
//First Button
if point_in_rectangle(mousex,mousey,0, 500, 125, 530) 
&& (hovering == 0 || hovering == 1)
{
    draw_set_alpha(0.8);
    hovering = 1;
}
else
{
    draw_set_alpha(0.5);
};
draw_set_color(c_gray);
draw_rectangle(0, 500, 125, 530, false);
draw_set_color(c_black);
draw_set_halign(fa_center);
draw_set_valign(fa_center);
draw_text(62.5,515,"Spaceship");

if mouse_check_button_pressed(mb_left) && hovering == 1 
{
    spaceship = true;
    technology = false;
    comms = false;
    objectives = false;
    audio_play_sound(buttonpress, .9, 0)
};
if spaceship == true
{
    draw_set_alpha(1);
    draw_set_halign(fa_left);
    draw_set_valign(fa_left);
    draw_text(10, 530, ("Colony Kits: " + string(obj_playerController.colonyKits)));
    draw_text(10, 550, ("Homing Missiles: " + string(obj_playerController.homingMissiles)));
    draw_text(10, 570, ("Scrap: " + string(obj_playerController.scrap)));
    draw_text(10, 590, ("Intel: " + string(obj_playerController.intel)));
    draw_set_halign(fa_center);
    draw_set_valign(fa_center);
    if point_in_rectangle(mousex,mousey, 215, 535, 325, 555)
    {
        draw_set_alpha(0.8);
        if mouse_check_button_pressed(mb_left)
        {
            audio_play_sound(buttonpress, .9, 0)
            if showEnergy = false showEnergy = true;
            else if showEnergy = true showEnergy = false;
        }
    }
    else
    {
        draw_set_alpha(0.5);
    }
    draw_set_colour(c_black);
    draw_rectangle(215, 535, 325, 555, false);
    draw_set_colour(c_white);
    draw_text(270, 545, "Show Energy");
    if point_in_rectangle(mousex, mousey, 215, 560, 325, 580)
    {
        draw_set_alpha(0.8);
        if mouse_check_button_pressed(mb_left)
        {
            audio_play_sound(buttonpress, .9, 0)
            if showShields = false showShields = true;
            else if showShields = true showShields = false;
        }
    }
    else
    {
        draw_set_alpha(0.5);
    }
    draw_set_colour(c_black);
    draw_rectangle(215, 560, 325, 580, false);
    draw_set_colour(c_white);
    draw_text(270, 570, "Show Shields");
    if point_in_rectangle(mousex, mousey, 215, 585, 325, 605)
    {
        draw_set_alpha(0.8);
        if mouse_check_button_pressed(mb_left)
        {
            audio_play_sound(buttonpress, .9, 0)
            if showHull = false showHull = true;
            else if showHull = true showHull = false;
        }
    }
    else
    {
        draw_set_alpha(0.5);
    }
    draw_set_colour(c_black);
    draw_rectangle(215, 585, 325, 605, false);
    draw_set_colour(c_white);
    draw_text(270, 595, "Show Hull");
};
hovering = 0;

//Second Button
if point_in_rectangle(mousex,mousey,125, 500, 250, 530) 
&& (hovering == 0 || hovering == 1)
{
    draw_set_alpha(0.8);
    hovering = 1;
}
else
{
    draw_set_alpha(0.5);
};
draw_set_color(c_gray);
draw_rectangle(125, 500, 250, 530, false);
draw_set_color(c_black);
draw_set_halign(fa_center);
draw_set_valign(fa_center);
draw_text(187.5,515,"Technology");

if mouse_check_button_pressed(mb_left) && hovering == 1 
{
    audio_play_sound(buttonpress, .9, 0)
    spaceship = false;
    technology = true;
    comms = false;
    objectives = false;
};
if technology == true
{
    intel = obj_playerController.intel;
    if obj_playerController.techengtree1 == false
    {
        draw_set_alpha(.8);
        draw_line_width(50, 565, 165, 565, 10);
        draw_set_alpha(0.5);
    }
    if obj_playerController.techmiltree1 == false
    {
        draw_set_alpha(.8);
        draw_line_width(295, 565, 410, 565, 10);
        draw_set_alpha(0.5);
    }
    
    if obj_playerController.techengtree1 == false
    {
        if point_in_rectangle(mousex, mousey, 0, 540, 100, 590) 
        && obj_playerController.techeng1 == false && obj_playerController.researching == false
            {
                draw_set_alpha(.8)
                if mouse_check_button_pressed(mb_left) && intel >= 50
                {
                    audio_play_sound(buttonpress, .9, 0)
                    obj_playerController.researching = true;
                    obj_playerController.researchingtecheng1 = true;
                    obj_playerController.alarm[4] = 600;
                    obj_playerController.intel -= 50;
                }
                if intel < 50
                {   
                    draw_set_colour(c_white);
                    draw_text(250, 480, "Insufficient intel!");
                    draw_set_colour(c_black);
                }
            }
            if obj_playerController.researchingtecheng1 = true
            {
                draw_set_alpha(1);
            }
            draw_sprite(spr_techeng1, -1, 50, 565);
            draw_set_alpha(0.5);
            
        if point_in_rectangle(mousex, mousey, 115, 540, 215, 590) 
        && obj_playerController.techeng1 == true && obj_playerController.researching == false
            {
                draw_set_alpha(.8)
                if mouse_check_button_pressed(mb_left) && intel >= 50
                {
                    audio_play_sound(buttonpress, .9, 0)
                    obj_playerController.researching = true;
                    obj_playerController.researchingtecheng2 = true;
                    obj_playerController.alarm[4] = 600;
                    obj_playerController.intel -= 50;
                }
                if intel < 50 && obj_playerController.techeng2 == false
                {
                    draw_set_colour(c_white);
                    draw_text(250, 480, "Insufficient intel!");
                    draw_set_colour(c_black);
                }
            }
            if obj_playerController.researchingtecheng2 = true
            {
                draw_set_alpha(1);
            }
            draw_sprite(spr_techeng2, -1, 165, 565);
            draw_set_alpha(0.5);
    }
    
    if obj_playerController.techmiltree1 == false
    {
        if point_in_rectangle(mousex, mousey, 245, 540, 345, 590) 
        && obj_playerController.techmil1 == false && obj_playerController.researching == false
            {
                draw_set_alpha(.8)
                if mouse_check_button_pressed(mb_left) && intel >= 50
                {
                    audio_play_sound(buttonpress, .9, 0)
                    obj_playerController.researching = true;
                    obj_playerController.researchingtechmil1 = true;
                    obj_playerController.alarm[4] = 600;
                    obj_playerController.intel -= 50;
                }
                if intel < 50
                {
                    draw_set_colour(c_white);
                    draw_text(250, 480, "Insufficient intel!");
                    draw_set_colour(c_black);
                }
            }
            if obj_playerController.researchingtechmil1 = true
            {
                draw_set_alpha(1);
            }
            draw_sprite(spr_techmil1, -1, 295, 565);
            draw_set_alpha(0.5);
            
        if point_in_rectangle(mousex, mousey, 360, 540, 460, 590) 
        && obj_playerController.techmil1 == true && obj_playerController.researching == false
            {
                draw_set_alpha(.8)
                if mouse_check_button_pressed(mb_left) && intel >= 50
                {
                    audio_play_sound(buttonpress, .9, 0)
                    obj_playerController.researching = true;
                    obj_playerController.researchingtechmil2 = true;
                    obj_playerController.alarm[4] = 150;
                    obj_playerController.intel -= 50;
                }
                if intel < 50 && obj_playerController.techmil2 == false
                {
                    draw_set_colour(c_white);
                    draw_text(250, 480, "Insufficient intel!");
                    draw_set_colour(c_black);
                }
            }
            if obj_playerController.researchingtechmil2 = true
            {
                draw_set_alpha(1);
            }
            draw_sprite(spr_techmil2, -1, 410, 565);
    }
    
    if obj_playerController.techengtree1 == true
    {
        if point_in_rectangle(mousex, mousey, 0, 540, 100, 590) 
        && obj_playerController.techeng3 == false && obj_playerController.researching == false
            {
                draw_set_alpha(.8)
                if mouse_check_button_pressed(mb_left) && intel >= 100
                {
                    audio_play_sound(buttonpress, .9, 0)
                    obj_playerController.researching = true;
                    obj_playerController.researchingtecheng3 = true;
                    obj_playerController.alarm[4] = 150;
                    obj_playerController.intel -= 100;
                }
            }
            if intel < 100
                {
                    draw_set_colour(c_white);
                    draw_text(250, 480, "Insufficient intel!");
                    draw_set_colour(c_black);
                }
            if obj_playerController.researchingtecheng3 = true
            {
                draw_set_alpha(1);
            }
            draw_sprite(spr_techeng3, -1, 50, 565);
            draw_set_alpha(0.5);
        }
    if obj_playerController.techmiltree1 == true
    {
        if point_in_rectangle(mousex, mousey, 245, 540, 345, 590) 
        && obj_playerController.techmil3 == false && obj_playerController.researching == false
            {
                draw_set_alpha(.8)
                if mouse_check_button_pressed(mb_left) && intel >= 100
                {
                    audio_play_sound(buttonpress, .9, 0)
                    obj_playerController.researching = true;
                    obj_playerController.researchingtechmil3 = true;
                    obj_playerController.alarm[4] = 150;
                    obj_playerController.intel -= 100;
                }
            }
            if intel < 100
                {
                    draw_set_colour(c_white);
                    draw_text(250, 480, "Insufficient intel!");
                    draw_set_colour(c_black);
                }
            if obj_playerController.researchingtechmil3 = true
            {
                draw_set_alpha(1);
            }
            draw_sprite(spr_techmil3, -1, 295, 565);
            draw_set_alpha(0.5);
    }
};
hovering = 0;

//Third Button
if point_in_rectangle(mousex,mousey,250, 500, 375, 530) 
&& (hovering == 0 || hovering == 1)
&& obj_spaceship.commsAvailable = true
{
    draw_set_alpha(0.8);
    hovering = 1;
}
else
{
    draw_set_alpha(0.5);
};
if (commsColonyTab || commsShipTab)
{
    if point_in_rectangle (mousex,mousey, 250, 500, 375, 530) && mouse_check_button_pressed(mb_left)
    {
    audio_play_sound(buttonpress, .9, 0)
    commsColonyTab = false;
    commsShipTab = false;   
    }
};
draw_set_color(c_gray);
draw_rectangle(250, 500, 375, 530, false);
draw_set_color(c_black);
draw_set_halign(fa_center);
draw_set_valign(fa_center);
draw_text(312.5,515,"Comms");

if mouse_check_button_pressed(mb_left) && hovering == 1 &&
   obj_spaceship.commsAvailable = true
{
    audio_play_sound(buttonpress, .9, 0)
    spaceship = false;
    technology = false;
    comms = true;
    objectives = false;
};
if comms == true
{
    draw_set_alpha(0.5);
    if obj_spaceship.commsFirstButton == true
    {
        if point_in_rectangle(mousex,mousey, 10, 540, 110, 590)
        {
            if mouse_check_button_pressed(mb_left) && commsColonyTab != true && commsShipTab != true
            {  
                audio_play_sound(buttonpress, .9, 0)
                commsShipTab = false;
                commsColonyTab = true;
            }
            else if mouse_check_button_pressed(mb_left) && commsColonyTab == true
            {
                audio_play_sound(buttonpress, .9, 0)
                commsColonyTab = false;
            }
            draw_set_alpha(0.8);
            hovering = 2;
        }
        else
        {
            draw_set_alpha(0.5);
        };
        if commsShipTab != true
        {
            draw_rectangle(10, 540, 110, 590, false);
            draw_set_halign(fa_center);
            draw_set_valign(fa_middle);
            draw_set_color(c_white);
            draw_text(60, 565, obj_spaceship.firstButtonName);
        }
        if commsColonyTab == true && obj_spaceship.commsFirstButton == true
        {
            if point_in_rectangle(mousex,mousey, 130, 540, 230, 590)
            {
                draw_set_alpha(0.8);
//
            }
            else
            {
                draw_set_alpha(0.5);
            }
            if obj_spaceship.firstButtonName == "Planet"
            {
                draw_set_color(c_black);
                draw_rectangle(130, 540, 230, 590, false);
                draw_set_halign(fa_center);
                draw_set_valign(fa_middle);
                draw_set_color(c_white); 
                draw_text(180, 560, "Teleport");
                if point_in_rectangle(mousex, mousey, 130, 540, 230, 590) && !instance_exists(obj_enemyFighter)
                && mouse_check_button_pressed(mb_left)
                {
                    if obj_doctorcontroller.teleported == false
                    {
                        obj_doctorcontroller.teleported = true;
                        audio_play_sound(buttonpress, .9, 0)
                        obj_doctorcontroller.alarm[1] = 30;
                    }
                }
                
            }
            else
            {
                if obj_spaceship.inst.upgd = false
                {
                    draw_set_color(c_black);
                    draw_rectangle(130, 540, 230, 590, false);
                    draw_set_halign(fa_center);
                    draw_set_valign(fa_middle);
                    draw_set_color(c_white); 
                    draw_text(180, 550, "Upgrade");
                    draw_text(180, 565, "Production");
                    draw_text(180, 580, ("Scrap: " + string(50)));
                }
                if point_in_rectangle(mousex, mousey, 130, 540, 230, 590) && mouse_check_button_pressed(mb_left)
                && obj_playerController.scrap >= 50
                {
                    obj_playerController.scrap -= 50;
                    obj_spaceship.inst.upgd = true;
                }
                else if point_in_rectangle(mousex, mousey, 130, 540, 230, 590) && obj_playerController.scrap < 50
                {
                    draw_text(250, 480, "Insufficient scrap!");
                }
            }
        }
    }
        if obj_spaceship.commsSecondButton == true
    {
        if point_in_rectangle(mousex,mousey, 130, 540, 230, 590)
        {
            draw_set_alpha(0.8);
        }
        else
        {
            draw_set_alpha(0.5);
        }
        if commsColonyTab != true && obj_spaceship.secondButtonName != "obj_finalportal"
        {
        draw_set_color(c_black);
        draw_rectangle(130, 540, 230, 590, false);
        draw_set_halign(fa_center);
        draw_set_valign(fa_middle);
        draw_set_color(c_white); 
        draw_text(180, 565, obj_spaceship.secondButtonName);
        }
        draw_set_color(c_black)
        if point_in_rectangle(mousex, mousey, 130, 540, 230, 590)
        {
            if mouse_check_button_pressed(mb_left) && commsShipTab != true && commsColonyTab != true
            {
                audio_play_sound(buttonpress, .9, 0)
                commsColonyTab = false;
                commsShipTab = true;
            }
            else if mouse_check_button_pressed(mb_left) && commsShipTab == true
            {
                audio_play_sound(buttonpress, .9, 0)
                commsShipTab = false;
            }            
        }
        if commsShipTab = true && instance_exists(obj_spaceship.instShip)
        {
        instShip = obj_spaceship.instShip;
            if point_in_rectangle(mousex,mousey, 250, 540, 350, 590)
            {
                draw_set_alpha(0.8);
                if mouse_check_button_pressed(mb_left)
                {
                    var aud = audio_play_sound(choose(snd_dronerespond1, snd_dronerespond2, snd_dronerespond3, snd_dronerespond4), 1, 0);
                    audio_sound_gain(aud, .8, 0);
                    if instShip.follow == false
                    {
                        instShip.follow = true;
                    }
                    else if instShip.follow == true
                    {
                        instShip.follow = false;
                    }
                }
            }
            else
            {
                draw_set_alpha(0.5);
            }
            draw_set_color(c_black);
            draw_rectangle(250, 540, 350, 590, false);
            draw_set_halign(fa_center);
            draw_set_valign(fa_middle);
            draw_set_color(c_white); 
            if instShip.follow == false
            {
                draw_text(300, 565, "Follow");
            }
            else if instShip.follow == true
            {
                draw_text(300, 565, "Stay");
            }
            if instShip.upgd == false
            {
                if point_in_rectangle(mousex,mousey, 370, 540, 470, 590)
                {
                    draw_set_alpha(0.8);
                    if mouse_check_button_pressed(mb_left) && obj_playerController.scrap >= 50
                    {
                        audio_play_sound(upgrade, .9, 0);
                        instShip.upgd = true;
                        obj_playerController.scrap -= 50;
                    }
                }
                else
                {
                    draw_set_alpha(0.5);
                }
                draw_set_color(c_black);
                draw_rectangle(370, 540, 470, 590, false);
                draw_set_halign(fa_center);
                draw_set_valign(fa_middle);
                draw_set_color(c_white); 
                draw_text(420, 550, "Upgrade");
                draw_text(420, 565, "Ally Ship");
                draw_text(420, 580, ("Scrap: " + string(50)));
            }
        }
    }
};
hovering = 0;
if comms = true && obj_spaceship.commsAvailable = false
{
    comms = false;
}
//Fourth Button
if point_in_rectangle(mousex,mousey,375, 500, 500, 530) 
&& (hovering == 0 || hovering == 1)
{
    draw_set_alpha(0.8);
    hovering = 1;
}
else
{
    draw_set_alpha(0.5);
};
draw_set_color(c_gray);
draw_rectangle(375, 500, 500, 530, false);
draw_set_color(c_black);
draw_set_halign(fa_center);
draw_set_valign(fa_center);
draw_text(437.5,515,"Objectives");

if mouse_check_button_pressed(mb_left) && hovering == 1 
{
    audio_play_sound(buttonpress, .9, 0)
    spaceship = false;
    technology = false;
    comms = false;
    objectives = true;
};
if objectives == true
{
    draw_set_colour(c_white);
    draw_set_alpha(1);
    draw_text(200, 540, "Current Objective: " + obj_playerController.currentObjective); 
    whiteDwarfDone = obj_playerController.whiteDwarfDone;
    brownDwarfDone = obj_playerController.brownDwarfDone;
    blackHoleDone = obj_playerController.blackHoleDone;
    if whiteDwarfDone
    {
        draw_set_alpha(1);
        coretext = "Collected";
    }
    else if !whiteDwarfDone
    {
        draw_set_alpha(0.8);
        coretext = "Not Collected";
    };
    draw_text(80, 555, "Superdense Core:");
    draw_text(80, 570, coretext);
    if brownDwarfDone
    {
        draw_set_alpha(1);
        coretext = "Collected";
    }
    else if !brownDwarfDone
    {
        draw_set_alpha(0.8);
        coretext = "Not Collected";
    };
    draw_text(380, 555, "Red Giant Energy:");
    draw_text(380, 570, coretext);
    if blackHoleDone
    {
        draw_set_alpha(1);
        coretext = "Collected";
    }
    else if !blackHoleDone
    {
        draw_set_alpha(0.8);
        coretext = "Not Collected";
    };
    draw_text(95, 595, "Superdense Plutonium");
    draw_text(80, 610, coretext);
    
};
hovering = 0;
draw_set_colour(c_black);
draw_set_alpha(1);
