<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Опросник HEI-2015: Оценка качества питания</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            background-color: #f8f9fa;
        }
        h1, h2 {
            color: #2c7fb8;
            text-align: center;
        }
        .instruction {
            background-color: #e8f4f8;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
            font-size: 0.95em;
        }
        .category {
            background-color: white;
            padding: 15px;
            margin-bottom: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }
        .question {
            margin-bottom: 15px;
        }
        .options {
            display: flex;
            flex-direction: column;
            gap: 8px;
            margin-top: 5px;
        }
        label {
            display: flex;
            align-items: center;
            padding: 8px;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.2s;
        }
        label:hover {
            background-color: #f0f0f0;
        }
        input[type="radio"] {
            margin-right: 10px;
        }
        .green { color: #28a745; font-weight: bold; }
        .yellow { color: #ffc107; font-weight: bold; }
        .red { color: #dc3545; font-weight: bold; }
        button {
            display: block;
            width: 100%;
            padding: 12px;
            background-color: #2c7fb8;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 1.1em;
            cursor: pointer;
            margin-top: 20px;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #1d6fa5;
        }
        #result {
            margin-top: 30px;
            padding: 20px;
            border-radius: 8px;
            text-align: center;
            font-size: 1.2em;
            display: none;
        }
        .good { background-color: #d4edda; color: #155724; }
        .medium { background-color: #fff3cd; color: #856404; }
        .bad { background-color: #f8d7da; color: #721c24; }
        .reset-btn {
            background-color: #6c757d;
            margin-top: 10px;
        }
        .reset-btn:hover {
            background-color: #5a6268;
        }
    </style>
</head>
<body>
    <h1>Опросник для оценки качества питания (HEI-2015, адаптированный для РФ)</h1>

    <div class="instruction">
        <strong>Инструкция:</strong> Отмечайте, как часто вы употребляете указанные продукты. В конце нажмите "Подсчитать баллы", чтобы узнать результат.
    </div>

    <form id="diet-form">
        <!-- Категория 1: Овощи и фрукты -->
        <div class="category">
            <h2>1. Овощи и фрукты</h2>
            
            <div class="question">
                <p>а) Сколько порций овощей вы едите в день? (1 порция ≈ 80 г сырых или 40 г приготовленных)</p>
                <div class="options">
                    <label><input type="radio" name="veg" value="5" required> 5+ порций</span></label>
                    <label><input type="radio" name="veg" value="3"> 3–4 порции</span></label>
                    <label><input type="radio" name="veg" value="0"> меньше 3</span></label>
                </div>
            </div>
            
            <div class="question">
                <p>б) Сколько цельных фруктов (не соков)?</p>
                <div class="options">
                    <label><input type="radio" name="fruits" value="5" required> 2+ порции</span></label>
                    <label><input type="radio" name="fruits" value="3"> 1 порция</span></label>
                    <label><input type="radio" name="fruits" value="0"> почти не ем</span></label>
                </div>
            </div>
            
            <div class="question">
                <p>в) Зелень (шпинат, салат) или бобовые (фасоль, чечевица)?</p>
                <div class="options">
                    <label><input type="radio" name="greens" value="5" required> ежедневно</span></label>
                    <label><input type="radio" name="greens" value="3"> 2–3 раза/неделю</span></label>
                    <label><input type="radio" name="greens" value="0"> редко</span></label>
                </div>
            </div>
        </div>

        <!-- Категория 2: Зерновые и молочные продукты -->
        <div class="category">
            <h2>2. Зерновые и молочные продукты</h2>
            
            <div class="question">
                <p>а) Цельнозерновые (гречка, овсянка, ржаной хлеб)?</p>
                <div class="options">
                    <label><input type="radio" name="grains" value="10" required> 3+ порции/день</span></label>
                    <label><input type="radio" name="grains" value="5"> 1–2 порции</span></label>
                    <label><input type="radio" name="grains" value="0"> белый хлеб/рис</span></label>
                </div>
            </div>
            
            <div class="question">
                <p>б) Молочные продукты (кефир, творог, сыр)?</p>
                <div class="options">
                    <label><input type="radio" name="dairy" value="10" required> 2+ порции/день</span></label>
                    <label><input type="radio" name="dairy" value="5"> 1 порция</span></label>
                    <label><input type="radio" name="dairy" value="0"> почти не употребляю</span></label>
                </div>
            </div>
        </div>

        <!-- Категория 3: Белки и жиры -->
        <div class="category">
            <h2>3. Белки и жиры</h2>
            
            <div class="question">
                <p>а) Рыба, курица, бобовые?</p>
                <div class="options">
                    <label><input type="radio" name="protein" value="5" required> 1–2 порции/день</span></label>
                    <label><input type="radio" name="protein" value="3"> 2–3 раза/неделю</span></label>
                    <label><input type="radio" name="protein" value="0"> редко</span></label>
                </div>
            </div>
            
            <div class="question">
                <p>б) Полезные жиры (оливковое/льняное масло, орехи)?</p>
                <div class="options">
                    <label><input type="radio" name="fats" value="10" required> ежедневно</span></label>
                    <label><input type="radio" name="fats" value="5"> 3–4 раза/неделю</span></label>
                    <label><input type="radio" name="fats" value="0"> почти не ем</span></label>
                </div>
            </div>
        </div>

        <!-- Категория 4: Ограничиваемые продукты -->
        <div class="category">
            <h2>4. Ограничиваемые продукты</h2>
            
            <div class="question">
                <p>а) Рафинированные продукты (белый хлеб, выпечка)?</p>
                <div class="options">
                    <label><input type="radio" name="refined" value="10" required> редко</span></label>
                    <label><input type="radio" name="refined" value="5"> 1–2 раза/неделю</span></label>
                    <label><input type="radio" name="refined" value="0"> почти каждый день</span></label>
                </div>
            </div>
            
            <div class="question">
                <p>б) Соль (солёные закуски, консервы)?</p>
                <div class="options">
                    <label><input type="radio" name="salt" value="10" required> минимум</span></label>
                    <label><input type="radio" name="salt" value="5"> умеренно</span></label>
                    <label><input type="radio" name="salt" value="0"> много</span></label>
                </div>
            </div>
            
            <div class="question">
                <p>в) Сахар (сладости, газировка)?</p>
                <div class="options">
                    <label><input type="radio" name="sugar" value="10" required> почти не ем</span></label>
                    <label><input type="radio" name="sugar" value="5"> иногда</span></label>
                    <label><input type="radio" name="sugar" value="0"> ежедневно</span></label>
                </div>
            </div>
            
            <div class="question">
                <p>г) Насыщенные жиры (жирное мясо, сливочное масло)?</p>
                <div class="options">
                    <label><input type="radio" name="saturated" value="10" required> редко</span></label>
                    <label><input type="radio" name="saturated" value="5"> умеренно</span></label>
                    <label><input type="radio" name="saturated" value="0"> часто</span></label>
                </div>
            </div>
        </div>

        <button type="button" id="calculate-btn">Подсчитать баллы</button>
    </form>

    <div id="result"></div>

    <script>
        document.getElementById('calculate-btn').addEventListener('click', function() {
            // Получаем значения всех выбранных ответов
            const veg = parseInt(document.querySelector('input[name="veg"]:checked').value);
            const fruits = parseInt(document.querySelector('input[name="fruits"]:checked').value);
            const greens = parseInt(document.querySelector('input[name="greens"]:checked').value);
            const grains = parseInt(document.querySelector('input[name="grains"]:checked').value);
            const dairy = parseInt(document.querySelector('input[name="dairy"]:checked').value);
            const protein = parseInt(document.querySelector('input[name="protein"]:checked').value);
            const fats = parseInt(document.querySelector('input[name="fats"]:checked').value);
            const refined = parseInt(document.querySelector('input[name="refined"]:checked').value);
            const salt = parseInt(document.querySelector('input[name="salt"]:checked').value);
            const sugar = parseInt(document.querySelector('input[name="sugar"]:checked').value);
            const saturated = parseInt(document.querySelector('input[name="saturated"]:checked').value);

            // Суммируем баллы
            const totalScore = veg + fruits + greens + grains + dairy + protein + fats + refined + salt + sugar + saturated;

            // Определяем оценку и рекомендацию
            let rating, recommendation, resultClass;
            
            if (totalScore >= 80) {
                rating = "Отлично!";
                recommendation = "Ваше питание сбалансировано и соответствует здоровым привычкам. Так держать!";
                resultClass = "good";
            } else if (totalScore >= 60) {
                rating = "Средний результат";
                recommendation = "Ваше питание неплохое, но есть куда стремиться. Обратите внимание на категории с низкими баллами.";
                resultClass = "medium";
            } else {
                rating = "Требует улучшений";
                recommendation = "Ваше питание нуждается в значительных изменениях. Рекомендуется проконсультироваться с диетологом.";
                resultClass = "bad";
            }

            // Формируем текст результата
            const resultText = `
                <h2>Ваш результат: ${totalScore} баллов из 100</h2>
                <p><strong>${rating}</strong></p>
                <p>${recommendation}</p>
                <button class="reset-btn" onclick="location.reload()">Пройти опрос заново</button>
            `;

            // Отображаем результат
            const resultDiv = document.getElementById('result');
            resultDiv.innerHTML = resultText;
            resultDiv.className = resultClass;
            resultDiv.style.display = 'block';

            // Прокручиваем страницу к результату
            resultDiv.scrollIntoView({ behavior: 'smooth' });
        });
    </script>
</body>
</html>
