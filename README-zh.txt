/**
 * @license
 * Copyright 2017-2023 kandao Inc
 * All Rights Reserved.
 */

KandaoPlayer网页全景播放器使用说明：
1.将kandaoplayer.js库文件放入服务器，在网页</body>结束标签前引入，src路径根据需要调整
  <script src="./kandaoplayer-1.0.6.js"></script>

2.在第1步引入脚本下方，添加如下播放器创建代码
  <script>
    const photo_player = new KandaoPlayer('container1', './assets/angra.jpg'); //图片
    const video_player = new KandaoPlayer('container2', './assets/MaryOculus.mp4', {stereo: 'h', video: {muted: true}}); //3D视频，左右
  </script>

  KandaoPlayer构造函数参数说明：
    参数1：HTML标签容器id
    参数2：全景图片或视频资源路径
      其中多分辨率视频需参照如下格式：
        {
          defaultResolution: 'HD',
          resolutions: [
              {
                  id: 'UHD',
                  label: 'Ultra high',
                  src: './assets/MaryOculus_UHD.mp4',
              },
              {
                  id: 'FHD',
                  label: 'High',
                  src: './assets/MaryOculus_FHD.mp4',
              },
              {
                  id: 'HD',
                  label: 'Standard',
                  src: './assets/MaryOculus_HD.mp4',
              },
              {
                  id: 'SD',
                  label: 'Low',
                  src: './assets/MaryOculus_HD.mp4',
              },
          ],
        }
    参数3: 播放器参数配置，对象类型（可选）
      1): 视角设置：fov: 180|360(默认)；
      2): 3D设置：stereo: undefined(默认)|'h'|'v'；
        undefined：默认平面素材
        'h':水平并置的3d素材
        'v':垂直并置的3d素材
      3): 交互控件设置，对象类型：
        widgets:{
          fullscreen: true(默认)|false, //是否启用全屏控件
          vr: true(默认)|false, //是否启用VR控件
          gyro: true(默认)|false, //是否启用陀螺仪控件
          gyroAutoPlay: 'off'(默认)|'on', //自动开启陀螺仪开关
          rotate: true|false(默认), //是否启用自旋转控件
          plane: true(默认)|false, //是否启用平面播放控件（只有视频资源有效）
        }
      4): 交互控件Icon设置，对象类型：
        icons:{
          fullscreen: './assets/fullscreen.svg', //icon image url
          vr: 'icon url',
          gyro: 'icon url',
          rotate: 'icon url',
          plane: 'icon url',
        }
      5): 自动旋转设置：autorotate: true|false(默认),当开启了widgets的rotate后，该设置不生效
      6): video属性设置，对象类型：
        video:{
          loop: true|false(默认), //是否循环播放
          muted: true|false(默认), //是否静音
          autoplay: true|false(默认), //是否自动播放，如果设置为true，视频会自动静音播放
          controls: true(默认)|false, //是否显示播放控制条
        }

  KandaoPlayer API说明：
    1. dispose():
      手动销毁播放器，示例：player.dispose();
    2. play():
      手动控制视频播放，示例：video_player.play();
    3. pause():
      手动控制视频暂停，示例：video_player.pause();
    4. toggleMute(true|false|undefined):
      手动切换视频静音，示例：video_player.toggleMute(true|false|undefined);
    5. toggleFullScreen():
      手动切换全屏，示例：player.toggleFullScreen();

Version: V1.0.5