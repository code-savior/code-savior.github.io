/**
  @license
  Copyright 2017-2023 kandao Inc
  All Rights Reserved.
*/

KandaoPlayer Web Panoramic Player Instructions:

1. Place the kandaoplayer.js library file on the server, and include it before the closing </body> tag of your webpage. Adjust the 'src' path as needed.

<script src="./kandaoplayer-1.0.6.js"></script>

2. Below the script tag from Step 1, add the following player creation code:

<script>
  const photo_player = new KandaoPlayer('container1', './assets/angra.jpg'); // For displaying a photo
  const video_player = new KandaoPlayer('container2', './assets/MaryOculus.mp4', {stereo: 'h', video: {muted: true}}); // For displaying a 3D video in left-right stereo format
</script>

KandaoPlayer Constructor Parameters Explanation:

  Parameter 1: HTML tag Container ID
  Parameter 2: Panorama image or video resource path
    The format for multi-resolution videos should follow as follows:
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
  Parameter 3: Player configuration parameters, object type (optional)
    1) Viewpoint Setting: fov: 180|360 (default);
    2) 3D Setting: stereo: undefined (default)|'h'|'v';
      undefined: Default flat material
      'h': Horizontal side-by-side 3D material
      'v': Vertical side-by-side 3D material
    3) Interaction Control Settings, object type:
      widgets:{
        fullscreen: true (default)|false, // Enable or disable fullscreen control
        vr: true (default)|false, // Enable or disable VR control
        gyro: true (default)|false, // Enable or disable gyroscope control
        gyroAutoPlay: 'off' (default)|'on', // Automatic gyroscope switch
        rotate: true|false (default), // Enable or disable autorotate control
        plane: true(default)|false, //Enable playback controls for the flat（video resources only）
      }
    4): Interaction Control Icon Settings, object type:
      icons:{
        fullscreen: './assets/fullscreen.svg', //icon image url
        vr: 'icon url',
        gyro: 'icon url',
        rotate: 'icon url',
        plane: 'icon url',
      }
    5) Autorotate Setting: autorotate: true|false (default), does not take effect when 'rotate' in 'widgets' is enabled
    6) Video Attribute Settings, object type:
      video:{
        loop: true|false(default), // Enable or disable loop playback
        muted: true|false(default), // Enable or disable mute
        autoplay: true|false(default), // Enable or disable autoplay,if set true it will auto mute
        controls: true(default)|false, // Show or hide video player controls
      }

KandaoPlayer API Documentation:

  1.dispose():
    Manually destroys the player, example: player.dispose();
  2.play():
    Manually play video, example: video_player.play();
  3.pause():
    Manually pause video, example: video_player.pause();
  4.toggleMute(true|false|undefined):
    Manually toggle video mute, example：video_player.toggleMute(true|false|undefined);
  5. toggleFullScreen():
    Manually toggle fullScreen, example：player.toggleFullScreen();

Version: V1.0.5