<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Control Net</title>
    <link rel="stylesheet" href="style/style.css">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/smoothscroll/1.4.10/SmoothScroll.min.js" integrity="sha256-huW7yWl7tNfP7lGk46XE+Sp0nCotjzYodhVKlwaNeco=" crossorigin="anonymous"></script>
</head>

<body>
    <div class="col">

        <p>Как пользоваться control Pictur</p>
        <p>(только для бота <a href="https://t.me/NovelAIDraw_bot" target="_blank">@NovelAIDraw_bot</a>)</p>

        <br>
        <br>

        <p>С февраля месяца, в боте Creation AI появилась такая кнопка</p>
        <div class="img_info_contairen">
            <img src="res/img/image-000.png" alt="">
        </div>

        <p>
            после нажатия на эту кнопку, бот попросит вас прислать фотографию/картинку. <span class="text_underline"> На этой картинке, бот будет угадывать границы объектов или персонажей, а затем генерировать изображение с учётом этих границ.</span>
        </p>

        <br>
        <br>

        <p>для наглядности и сравнения результатов генерации, я буду использовать одну картинку в качестве "исходника</p>
        <div class="img_info_contairen">
            <img src="res/img/image-001.jpg" alt="">
            <p>(исходник для генераций)</p>
        </div>

        <br>

        <p>а в качестве тегов и модели, буду использовать следующее: masterpiece, best quality, Girl, red hair, red eyes, wicked smile, dark clothes. <br> model: Anime4 (AnythingV5)
        </p>

        <br>
        <br>

        <h1>1.Генерация по фото</h1>

        <br>

        <p>Итак, после загрузки картинки, бот покажет четыре кнопки:</p>

        <div class="img_info_contairen">
            <img src="res/img/image-002.png" alt="">
        </div>
        <p>нижние думаю вам интуитивно понятны (удалить картинку и подтвердить настройки) Теперь касательно двух верхних: при выборе функций, крайне важно соблюдать “пару” между preprocessor и processor сейчас объясню почему: Preprocessor будет указывать,
            какой режим нужно применить на загруженной картинке. Говоря проще, какую “маску” должна сделать нейросеть. Processor будет ПРИМЕНЯТЬ полученную маску, для генерации своего изображения, с учетом тегов пользователя. то есть выбрав Canny в первом,
            вы также должны выбрать Canny во втором. 
        </p>

        <br>

        <p>ПРЕДУПРЕЖДЕНИЕ: После загрузки картинки, бот самостоятельно поправит размер картинки в настройках, <span class="text_underline">не рекомендую уменьшать или увеличивать размер</span>, иначе результат генерации будет хуже.</p>

        <br>


        <h1>1.1 Режим работы</h1>

        <br>

        <p>Теперь поговорим поподробнее про preprocess:</p>

        <div class="img_info_contairen">
            <img src="res/img/image-003.png" alt="">
        </div>

        <p>всего их здесь 35 штук (не считая none, так как оно выключает preprocess). </p>
		
		 <div class="img_info_contairen">
            <img src="res/img/image-001.1.png" alt="">
			<p> это список кнопок в process </p>
        </div>

		<h1>1.2 Результаты генераций:</h1>
		<p> Ниже я покажу сгенерированный результат, а правее будет маска, которая получилась после работы preprocess. в скобках будет название кнопки в process.</p>
        <div class="img_info_contairen">
            <p>1 Canny(canny-v1.1)</p>
            <img src="res/img/image-004.png" alt="">
        </div>

        <br>

        <div class="img_info_contairen">
            <p>depth(depth-v1.1)</p>
            <img src="res/img/image-005.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>depth_zoe (process: depth-v1.1)</p>
            <img src="res/img/image-006.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>hed(softedge-v1.1)</p>
            <img src="res/img/image-007.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>hed_safe (softedge-v1.1)</p>
            <img src="res/img/image-008.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>hed (softedge-v1.1)</p>
            <img src="res/img/image-009.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>Openpose(и все остальные с этой приставкой)</p>
        </div>

        <p>для следующего режима, нужно изменить исходник из за близкого расстояния бот не может угадать позу персонажа) для того чтобы изменить исходную картинку нужно нажать “del control picture” ( а для
            смены режима работы controlnet “Edit control picture”
        </p>

        <div class="img_info_contairen">
            <img src="res/img/image-010.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>На этот раз загрузим вот такую стоковую картинку</p>
            <img src="res/img/image-011.png" alt="">
        </div>

        <p>
            затем в preprocess и process выбираем openpose
        </p>

        <div class="img_info_contairen">
            <p>Openpose(openpose-v1.1)</p>
            <img src="res/img/image-012.png" alt="">
        </div>

        <p>
            как видите, результат иногда выходит хуже. Обычно это происходит из за того что бот не смог угадать объект на картинке. Решением такой проблемы будет либо переключение модели обработки, либо замена исходной картинки.
        </p>

        <div class="img_info_contairen">
            <p>Openpose_hand (process: openpose-v1.1)</p>
        </div>

        <p>
            Для этого режима, я выбрал модель Anime3 (CamelliaMix) так как у нее лучше и чаще всего получаются “правильные” пальцы/руки
        </p>

        <div class="img_info_contairen">
            <img src="res/img/image-013.png" alt="">
        </div>

        <p>openpose_face/faceonly/full я оставлю для следующего гайда, в котором подробнее разберу все режимы openpose, здесь я лишь показал возможности этой функции</p>

        <br>

        <div class="img_info_contairen">
            <p>
                Pidinet (softedge-v1.1)
            </p>
        </div>

        <p>
            теги и исходник те же что в начале гайда
        </p>

        <div class="img_info_contairen">
            <img src="res/img/image-016.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>
                 pidinet_safe (softedge-v1.1)
            </p>
            <img src="res/img/image-017.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>
                 pidinet_sketch (softedge-v1.1)
            </p>
            <img src="res/img/image-018.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>
                 pidinet_scribble (softedge-v1.1)
            </p>
            <img src="res/img/image-019.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>
                scribble_xdog (scribble-v1.1)
            </p>
            <img src="res/img/image-020.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>
               scribble_hed (softedge-v1.1)
            </p>
            <img src="res/img/image-021.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>
               segmentation(seg-v1.1)
            </p>
            <img src="res/img/image-022.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>
                oneformer_coco (seg-v1.1)
            </p>
            <img src="res/img/image-023.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>
                oneformer_ade20k (seg-v1.1)
            </p>
            <img src="res/img/image-024.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>
               normal_bae (normalbae-v1.1)
            </p>
            <img src="res/img/image-025.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>
                lineart (lineart-v1.1)
            </p>
            <img src="res/img/image-026.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>
                lineart_coarse (lineart-v1.1)
            </p>
            <img src="res/img/image-027.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>
                lineart_anime (lineart anime-v1.1)
            </p>
            <img src="res/img/image-028.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>
                lineart_standard (lineart-v1.1)
            </p>
            <img src="res/img/image-029.png" alt="">
        </div>

        <div class="img_info_contairen">
            <p>
                shuffle (process: shuffle-v1.1)
            </p>
            <img src="res/img/image-030.png" alt="">
        </div>

        <h1>2. Генерация по маске</h1>

        <br>

        <p>
            Наконец то мы подошли к интересному. На картинках выше вы видели арт и маску рядом, так было сделано для вашего удобства, чтобы вы могли сравнить. А теперь самое интересное: эти маски можно использовать повторно, если допустим вы хотите использовать определённую
            позу персонажа, или протестировать другие теги с фиксированной позицией объектов (персонаж выглядывающий из за угла стены, или приветствующий зрителя, примеров может быть бесконечно)
        </p>

        <br>
        <br>

        <p>
            для того чтобы использовать маску, достаточно отправить ее вместо картинки после нажатия на control picture (Контроль картинки, если у вас бот на русском языке.) и выбрать preprocess: none (тут он не нужен, потому что мы уже загрузили боту маску) process
            необходимо выставить в соответствии с загруженной маской (если маска от canny, то выбирайте canny) в остальном: теги, модель, выборка, и т.д в вашем распоряжении, однако менять размеры не рекомендуется, бот всё равно отрисует в границах маски,
            а вот за его пределами всё будет однотонным цветом.
        </p>
        <div class="img_info_contairen">
            <img src="res/img/image-031.png" alt="">
        </div>

        <p>
            Для теста, я взял маску canny, и изменил теги. Теперь у меня фиолетово-волосая девочка с зелеными глазами.
        </p>

        <div class="img_info_contairen_text_normal">
            <p>
                Результат:
            </p>
            <img src="res/img/image-032.png" alt="">
        </div>
        <p>
            Как видите, сохранилась поза персонажа, и все остальное, кроме конечно же образа. В общем, подобрав подходящую маску, вы можете генерировать разных персонажей, сохраняя при этом определённые детали.
        </p>

        <br>
        <br>

        <div class="livehack">
            <h2 style="margin: 0 0 0 20px;">Лайфхак:</h2>
        </div>

        <br>

        <p>А что если вам не нравится определённая деталь на фотографии? К примеру, вам понравится сидящий персонаж, но вон тот меч в углу вам не подходит?
            <span class="text_underline">Можно отредактировать маску</span>. Просто закрасьте черным цветом ту область, которая не подходит для вашей задумки, а если вы владеете художественными навыками, то и вовсе можете дорисовать свои детали.
        </p>
        <div class="img_info_contairen_text_normal">
            <p>
                Результат:
            </p>
            <img src="res/img/image-033.png" alt="">
        </div>
        <p>
            На маске справа, я затер фоновые детали, а также убрал открытый рот. из за удаления этих деталей, бот нарисовал некую комнату с окном на фоне. А рот теперь нарисован закрытым ( я забыл написать какой нибудь тег для этого)
        </p>
        <p>
            Это будет работать с такими масками как canny, hed,pidinet, scrible, и вариациями lineart.
        </p>

        <br>
        <br>

        <h1>
            ВЫВОД
        </h1>

        <br>
        <div>
            <p>
                В целом, это довольно интересная возможность генерировать картинки с определёнными объектами, или персонажами. И даже если потребуется более тонкий результат, можно отредактировать маску, затерев или добавив деталей для получения "качественной" картинки
            </p>
			
			<p>
               К сожалению я показал вам лишь около половины моделей, потому что все остальные не имеют нужных иструментов для работы. Так что не советую их выбирать ибо в таком случае вы в пустую потратите генерацию. 
            </p>
			
            <p>
                Однако, некоторые из них не работали, а другие требовали дополнительной модели для работы (чего не было у бота).
            </p>
           
            <br>

            <p>
                На этом у меня собственно всё! Я постарался затронуть больше режимов, и показать результаты генераций, не меняя настроек. чтобы вы для себя сравнили результаты.
            </p>

            <br>

            <p>
                Всего вам доброго! Удачных генераций! Гайд писал
                <a href="https://t.me/ZeroHuk0" target="_blank">@ZeroHuk0</a>
            </p>
        </div>

    </div>
</body>

</html>
