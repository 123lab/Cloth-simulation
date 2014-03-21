
1. Compare to the Jello simluation, what are the advantages of using PBD over using mass-spring system?
The advantages of using PBD are (1) PBD gives control over explicit integration and removes the typical instability problems. (2) Positions of vertices and parts of objects can directly be manipulated during the simulation. (3) The explicit position based solver is easy to understand and implement.

2. What is the function of the stiffness for each constraint? What value will you use for simulating a rigid body?
The stiffness parameter defines the strength of the constraint. For simulating a rigid body, the value should be 1.

3. The collision detection system used in PBD combined both continuous collision and static collision detection. Explain in short the difference between these two mechanisms. Which mechanism is used in Jello simulation(detecting, not resolving)?
If the ray x->p enters the object, we use continuous collision detection, but if the ray lies completely inside and object, we use static collision detection.
In Jello simulation, we use static collision.

4. Does your stretch constraint resolving preserve momentum? What about fixed point constraint and collision constraint? Why?
Stretch constraint resolving preserves momentum. Because it is internal constraints and there is no impulse transferred to the particles. Fixed point constraint and collision constraint do not preserve momentum. Because there is external forces added to the particles.  

5. Which part of the PBD concept cost you most of time in understanding? Which part cost most in implementing?
To me, constraint projection costs me most of time in understanding while the velocity damping costs most in implementing.


Here's what I implemented in the project code:
1. In ClothSim::generate_internal_constraints(), implemented fixedpoint, stretch, bend constraints.

2. Main loop for PBD:
ClothSim::apply_external_force()
ClothSim::compute_predicted_position() 
ClothSim::integration() 
ClothSim::update_velocity()

3. Damp the velocity: ClothSim::damp_velocity()

4. Resolve constraints:
FixedPointConstraint::project_constraint()
StretchConstraint::project_constraint()
CollisionConstraint::project_constraint()

5. Collision detection: Sphere::line_intersection()
 
Videos are included in the folder "Output_Videos".

If you have any questions, please feel free to contact me: zimengy@seas.upenn.edu




