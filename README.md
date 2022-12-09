<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>MediaElement.js 4.2.x - audio/video unification library</title>
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
    <link rel="icon" href="favicon.ico" type="image/x-icon">

    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/5.0.0/normalize.min.css">
    <link rel="stylesheet" href="../build/mediaelementplayer.css">

    <style>

        html, body {
            overflow-x: hidden;
        }

        #container {
            padding: 0 20px 50px;
        }
        .error {
            color: red;
        }
        a {
            word-wrap: break-word;
        }

        code {
            font-size: 0.8em;
        }

        #player2-container .mejs__time-buffering, #player2-container .mejs__time-current, #player2-container .mejs__time-handle,
        #player2-container .mejs__time-loaded, #player2-container .mejs__time-hovered, #player2-container .mejs__time-marker, #player2-container .mejs__time-total {
            height: 2px;
        }

        #player2-container .mejs__time-total {
            margin-top: 9px;
        }
        #player2-container .mejs__time-handle {
            left: -5px;
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: #ffffff;
            top: -5px;
            cursor: pointer;
            display: block;
            position: absolute;
            z-index: 2;
            border: none;
        }
        #player2-container .mejs__time-handle-content {
            top: 0;
            left: 0;
            width: 12px;
            height: 12px;
        }
    </style>
</head>

<body>

    <div id="container">
        <section>
        <h1>MediaElement.js</h1>

        <h2><em>audio/video</em> unification library</h2>

        <p><em>MediaElement</em> is a wrapper that mimics the native HTML5 MediaElement syntax (get/set) as a renderer that
            can handle media from HTML5, YouTube, Vimeo, Soundcloud, Flash, Facebook, and other libraries.</p>

        <p><em>MediaElementPlayer</em> is built off of MediaElement and creates a fully featured player on top of the
            unified syntax from MediaElement.</p>
        </section>

        <section>
            <h3>Global Options</h3>
            <form action="#" method="get">
                <label>Language <select name="lang">
                    <option value="ca">Català / Catalan (ca)</option>
                    <option value="cs">Čeština / Czech (cs)</option>
                    <option value="de">Deutsch / German (de)</option>
                    <option value="en" selected>English (en)</option>
                    <option value="es">Español / Spanish; Castilian (es)</option>
                    <option value="fa">فارسی / Persian (fa)</option>
                    <option value="fr">Français / French (fr)</option>
                    <option value="hr">Hrvatski / Croatian (hr)</option>
                    <option value="hu">Magyar / Hungarian (hu)</option>
                    <option value="it">Italiano / Italian (it)</option>
                    <option value="ja">日本語 / Japanese (ja)</option>
                    <option value="ko">한국어 / Korean (ko)</option>
                    <option value="ms">Melayu / Malay (ms)</option>
                    <option value="nl">Nederlands / Dutch (nl)</option>
                    <option value="pl">Polski / Polish (pl)</option>
                    <option value="pt">Português / Portuguese (pt)</option>
                    <option value="ro">Română / Romanian (ro)</option>
                    <option value="ru">Русский / Russian (ru)</option>
                    <option value="sk">Slovensko / Slovak (sk)</option>
                    <option value="sv">Svenska / Swedish (sv)</option>
                    <option value="uk">Українська / Ukrainian (uk)</option>
                    <option value="zh">繁体中文 / Traditional Chinese (zh-TW)</option>
                    <option value="zh-CN">简体中文 / Simplified Chinese (zh-CN)</option>
                </select>
                </label>
                <label>Stretching (Video Only)<select name="stretching">
                    <option value="auto" selected>Auto (default)</option>
                    <option value="responsive">Responsive</option>
                    <option value="fill" selected>Fill</option>
                    <option value="none" selected>None (original dimensions)</option>
                </select>
                </label>
            </form>
        </section>

        <br>
        <div class="players" id="player1-container">

            <h3>Video Player</h3>

            <div class="media-wrapper">
                <video id="player1" width="640" height="360" style="max-width:100%;" poster="http://www.mediaelementjs.com/images/big_buck_bunny.jpg" preload="none" controls playsinline webkit-playsinline>
                    <source src="https://commondatastorage.googleapis.com/gtv-videos-bucket/CastVideos/mp4/BigBuckBunny.mp4" type="video/mp4">
                    <track srclang="en" kind="subtitles" src="mediaelement.vtt">
                    <track srclang="en" kind="chapters" src="chapters.vtt">
                </video>
            </div>
            <br>
            <div>
                <label>Sources <select name="sources">
                    <option value="//github.com/mediaelement/mediaelement-files/blob/master/big_buck_bunny.mp4?raw=true">MP4</option>
                    <option value="//upload.wikimedia.org/wikipedia/commons/2/22/Volcano_Lava_Sample.webm">WebM</option>
                    <option value="https://vips-livecdn.fptplay.net/hda1/vtv6hd_vhls.smil/chunklist_b2500000.m3u8">HLS</option>
                    <option value="//www.bok.net/dash/tears_of_steel/cleartext/stream.mpd">M(PEG)-DASH</option>
                    <option value="https://www.dailymotion.com/video/x11prnt">DailyMotion</option>
                    <option value="https://www.youtube.com/watch?v=twYp6W6vt2U">YouTube</option>
                    <option value="https://player.vimeo.com/video/108018156?title=0&amp;byline=0&amp;portrait=0&amp;badge=0">Vimeo</option>
                    <option value="https://www.facebook.com/peopleareawesome/videos/1542174665831706/">Facebook</option>
                    <option value="https://www.twitch.tv/videos/109010497">Twitch</option>
                </select>
                </label>
            </div>
            <br>
            <div class="player-info">
                <h4>Player information</h4>
                <div id="player1-rendername">
                    <p><strong>Source</strong>: <span class="src"><a href="https://commondatastorage.googleapis.com/gtv-videos-bucket/CastVideos/mp4/BigBuckBunny.mp4" target="_blank">https://commondatastorage.googleapis.com/gtv-videos-bucket/CastVideos/mp4/BigBuckBunny.mp4</a></span></p>
                    <p><strong>Renderer</strong>: <span class="renderer">html5</span></p>
                    <p class="error"></p>
                </div>
            </div>
        </div>

        <br>
        <hr>

        <div class="players" id="player2-container">

            <h3>Audio Player</h3>

            <p>By default, time handle element is hidden, but in this demo the following styles were added to display it just for audio:</p>

            <pre><code>
#player2-container .mejs__time-buffering,
#player2-container .mejs__time-current,
#player2-container .mejs__time-handle,
#player2-container .mejs__time-loaded,
#player2-container .mejs__time-marker,
#player2-container .mejs__time-total,
#player2-container .mejs__time-hovered {
    height: 0.125rem;
}

#player2-container .mejs__time-total {
    margin-top: 0.5625rem;
}
#player2-container .mejs__time-handle {
    left: -0.3125rem;
    width: 0.75rem;
    height: 0.75rem;
    border-radius: 50%;
    background: #ffffff;
    top: -0.3125rem;
    cursor: pointer;
    display: block;
    position: absolute;
    z-index: 2;
    border: none;
}
#player2-container .mejs__time-handle-content {
    top: 0;
    left: 0;
    width: 0.75rem;
    height: 0.75rem;
}
            </code></pre>

            <div class="media-wrapper">
                <audio id="player2" preload="none" controls style="max-width:100%;">
                    <source src="http://www.largesound.com/ashborytour/sound/AshboryBYU.mp3" type="audio/mp3">
                </audio>
            </div>
            <br>
            <div>
                <label>Sources <select name="sources">
                    <option value="https://github.com/mediaelement/mediaelement-files/blob/master/AirReview-Landmarks-02-ChasingCorporate.mp3?raw=true">MP3</option>
                    <option value="https://commons.wikimedia.org/wiki/File:Demo_chorus.ogg">OGG</option>
                    <option value="http://db3.indexcom.com/bucket/ram/00/05/64k/05.m3u8">HLS</option>
                    <!--<option value="rtmp://s3b78u0kbtx79q.cloudfront.net/cfx/st/mp3:fake_empire-cbr">RTMP</option>-->
                    <option value="https://w.soundcloud.com/player/?url=https%3A//api.soundcloud.com/tracks/282715465&amp;auto_play=false&amp;hide_related=false&amp;show_comments=true&amp;show_user=true&amp;show_reposts=false&amp;visual=true">SoundCloud</option>
                    <!--<option value="https://api.soundcloud.com/tracks/323195515/stream?client_id=95f22ed54a5c297b1c41f72d713623ef">SoundCloud</option>-->
                </select>
                </label>
            </div>
            <br>
            <div class="player-info">
                <h4>Player information</h4>
                <div id="player2-rendername">
                    <p><strong>Source</strong>: <span class="src"><a href="http://www.largesound.com/ashborytour/sound/AshboryBYU.mp3" target="_blank">http://www.largesound.com/ashborytour/sound/AshboryBYU.mp3</a></span></p>
                    <p><strong>Renderer</strong>: <span class="renderer">html5</span></p>
                    <p class="error"></p>
                </div>
            </div>

        </div>
    </div>

    <script src="../build/mediaelement-and-player.js"></script>
    <script src="../build/renderers/dailymotion.js"></script>
    <script src="../build/renderers/facebook.js"></script>
    <script src="../build/renderers/soundcloud.js"></script>
    <script src="../build/renderers/twitch.js"></script>
    <script src="../build/renderers/vimeo.js"></script>
    <script src="../build/lang/cs.js"></script>
    <script src="../build/lang/de.js"></script>
    <script src="../build/lang/es.js"></script>
    <script src="../build/lang/fa.js"></script>
    <script src="../build/lang/fr.js"></script>
    <script src="../build/lang/hr.js"></script>
    <script src="../build/lang/hu.js"></script>
    <script src="../build/lang/it.js"></script>
    <script src="../build/lang/ja.js"></script>
    <script src="../build/lang/ko.js"></script>
    <script src="../build/lang/ms.js"></script>
    <script src="../build/lang/nl.js"></script>
    <script src="../build/lang/pl.js"></script>
    <script src="../build/lang/pt.js"></script>
    <script src="../build/lang/ro.js"></script>
    <script src="../build/lang/ru.js"></script>
    <script src="../build/lang/sk.js"></script>
    <script src="../build/lang/sv.js"></script>
    <script src="../build/lang/uk.js"></script>
    <script src="../build/lang/zh-cn.js"></script>
    <script src="../build/lang/zh.js"></script>
    <script src="demo.js"></script>
</body>
</html>
