# Unity-FFmpeg-Livebroadcast-Nginx-Rtmp
Use FFmpeg Livebroadcast Unity Camera Frame on Nginx Rtmp



Changed Script "FFmpegSession.cs"

public static FFmpegSession CreateWithOutputPath(
            string outputPath,
            int width, int height, float frameRate,
            FFmpegPreset preset
        )
        {
            return new FFmpegSession(
                "-f rawvideo -vcodec rawvideo -pixel_format rgba"
                + " -colorspace bt709"
                + " -video_size " + width + "x" + height
                + " -framerate " + frameRate
                + " -loglevel warning -i - " + preset.GetOptions()
                + " -vcodec libx264 -acodec copy -preset:v ultrafast -tune:v zerolatency -f flv rtmp://......"   //add you rtmp server url
            //+ " \"" + outputPath + "\""
            );
        }
