新增雷达融合模块，需要正确的mavlink消息才可以解析，下面为雷达的xml消息

<message id="16000" name="RADAR_ODOMETRY">
  <description>Radar Odometry message to communicate odometry information with an external interface. Fits ROS REP 147 standard for aerial vehicles (http://www.ros.org/reps/rep-0147.html).</description>
  <field type="uint64_t" name="time_usec" units="us">Timestamp (UNIX Epoch time or time since system boot). The receiving end can infer timestamp format (since 1.1.1970 or since system boot) by checking for the magnitude of the number.</field>
  <field type="float[3]" name="p_local" units="m">uav position in global frame</field>
  <field type="float[3]" name="v_local" units="m">uav velocity in global frame</field>
  <field type="float[4]" name="q"> Quaternion from body to global: w,x,y,z (1 0 0 0 is the null-rotation)</field>
  <field type="float[3]" name="v_body" units="m/s">uav velocity in body frame</field>
  <field type="float[3]" name="p_local_std">Roll angular speed</field>
  <field type="float[3]" name="v_local_std">Pitch angular speed</field>
  <field type="float[3]" name="v_body_std">Type of estimator that is providing the odometry.</field>
  <field type="uint8_t" name="is_valid">radar odom valid type</field>
</message>

同时需要注意kconfig打开雷达模块，并配置EKF2_ER_** 雷达相关参数
