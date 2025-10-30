
# 준비

`lerobot/src/lerobot/robots` 폴더에 `bi_so101_follower` 폴더를 넣어주세요.

`lerobot/src/lerobot/teleoperators` 폴더에 `bi_so101_leader` 폴더를 넣어주세요.

그리고 다시 설치를 진행합니다.

```
pip install -e .
```

# 텔레오퍼레이션 실행 

## 1. 카메라 없이

```bash
python -m lerobot.teleoperate \
  --robot.type=bi_so101_follower \
  --robot.left_arm_port=/dev/ttyACM2 \
  --robot.right_arm_port=/dev/ttyACM3 \
  --robot.id=bimanual_so101_follower \
  --teleop.type=bi_so101_leader \
  --teleop.left_arm_port=/dev/ttyACM0 \
  --teleop.right_arm_port=/dev/ttyACM1 \
  --teleop.id=bimanual_so101_leader \
  --display_data=false
```

## 2. 카메라와 함께

```bash
python -m lerobot.teleoperate \
  --robot.type=bi_so101_follower \
  --robot.left_arm_port=/dev/ttyACM2 \
  --robot.right_arm_port=/dev/ttyACM3 \
  --robot.id=bimanual_so101_follower \
  --teleop.type=bi_so101_leader \
  --teleop.left_arm_port=/dev/ttyACM0 \
  --teleop.right_arm_port=/dev/ttyACM1 \
  --teleop.id=bimanual_so101_leader \
  --display_data=true \
  --robot.cameras='{    
    left:  {type: opencv, index_or_path: 2, width: 640, height: 480, fps: 25},
    right: {type: opencv, index_or_path: 4, width: 640, height: 480, fps: 25}
  }'

```