# ariac conveyor tracking update
1.	fudge_wait_time change to 3.0; q_rail_start change to 2.7.
2.	CONVEYOR_TRACK_FUDGE_TIME≈0.5 is caused by the delay from receiving goal. Replaced it with dt=start_time-part_header_time; for the exact time.
3.	Change docking position limit from 0 to -1.7 (but never been tested, the goal always wants the part from the beginning of the conveyor)
4.	Change the intermediate pose to agv2 cruise pose, and only execute 1/3 of it,   ros::Duration(dt_move/3).sleep(); it is enough to move robot away from the obstacle so that the robot can rotate its arm without hitting things.
5.	Delete the intermediate pose After robot placed the part on the agv. Robot will start tracking immediately. It will not collide with obstacle.

Usage: just replace the file
