# ffmpeg-
短视频剪辑
常用命令

添加字幕
ffmpeg -i out.mp4 -vf subtitles=out.srt output.mp4

添加水印
水印局中
ffmpeg -i out.mp4 -i sxyx2008@163.com.gif -filter_complex overlay="(main_w/2)-(overlay_w/2):(main_h/2)-(overlay_h)/2" output.mp4
参数解释

-i out.mp4(视频源)
-i sxyx2008@163.com.gif(水印图片)
overlay 水印的位置
output.mp4 输出文件
