# ffmpeg-短视频剪辑常用命令

# 添加字幕
ffmpeg -i out.mp4 -vf subtitles=out.srt output.mp4

# 添加水印
水印局中
ffmpeg -i out.mp4 -i sxyx2008@163.com.gif -filter_complex overlay="(main_w/2)-(overlay_w/2):(main_h/2)-(overlay_h)/2" output.mp4
参数解释

-i out.mp4(视频源)
-i sxyx2008@163.com.gif(水印图片)
overlay 水印的位
output.mp4 输出文件


# 你可以使用 -aspect 标志设置一个视频文件的屏幕高宽比，像下面。

$ ffmpeg -i input.mp4 -aspect 16:9 output.mp4



# 增加/减少视频播放速度
FFmpeg 允许你调整视频播放速度。

为增加视频播放速度，运行：

$ ffmpeg -i input.mp4 -vf "setpts=0.5*PTS" output.mp4


# 提取视频中的音频内容 https://bbs.huaweicloud.com/blogs/331588
如果想要把目标视频中的某段音频截取出来，可以使用如下代码

from moviepy.editor import *

clip = VideoFileClip('./1644974996.mp4').subclip(10, 20)

audioclip1 = clip.audio  # 从视频对象中提取音频
audioclip1.write_audiofile('a.mp3')  # 写入音频文件

# 截取视频封面
很多时候我们需要生成视频的封面，直接使用下述几行代码，即可实现。

from moviepy.editor import *

clip = VideoFileClip('./1644974996.mp4')

clip.save_frame("frame.jpg")  # 保存第1帧
clip.save_frame("frame.png", t=2)  # 保存2s时刻的那1帧


# 设置视频倍速播放
读取视频，调用 speedx() 方法，其中设置要加速到的倍数。

from moviepy.editor import *
clip = VideoFileClip('./1644974996.mp4')

video_1 = clip.speedx(2)
video_1.write_videofile('sss.mp4')

# 提取A视频的音频，注入到B视频中
from moviepy.editor import *

 读取2个视频文件 
videoclip_a = VideoFileClip("1644974996.mp4")
videoclip_b = VideoFileClip("1644974998.mp4")

 提取A视频文件的音频部分
audio_a = videoclip_a.audio

 给B设置音频，注意视频最终合成的大小会依据长的为准
videoclip_c = videoclip_b.set_audio(audio_a)

 输出新的视频文件
videoclip_c.write_videofile("videoclip_c.mp4")
