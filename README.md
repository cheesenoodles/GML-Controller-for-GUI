# GML-Controller-for-GUI
if showEnergy == true
{
    energy = obj_spaceship.energy; //ENERGY BAR
    draw_set_alpha(.5);
    draw_set_color(c_blue);
    draw_rectangle(0, 15, 210, 45, true);
    draw_set_color(c_red);
    draw_rectangle(0, 20, ((energy/20)*204), 40, false);
    draw_set_color(c_yellow);
    draw_text(105, 30, "Energy: " + string(energy));
}

if showShields == true
{
    shields = obj_spaceship.shields; //SHIELD BAR
    draw_set_alpha(.5);
    draw_set_color(c_blue);
    draw_rectangle(0, 55, 210, 85, true);
    draw_set_color(c_red);
    draw_rectangle(0, 60, ((shields/5)*170), 80, false);
    draw_set_color(c_yellow);
    draw_text(105, 70, "Shields: " + string(shields));
    draw_set_color(c_black);
}

if showHull == true
{
    hull = obj_spaceship.hull; //HULL BAR
    draw_set_alpha(.5);
    draw_set_color(c_blue);
    draw_rectangle(0, 95, 210, 125, true);
    draw_set_color(c_red);
    draw_rectangle(0, 100, ((hull/100)*203), 120, false);
    draw_set_color(c_yellow);
    draw_text(105, 110, "Hull: " + string(hull));
    draw_set_color(c_black);
}
