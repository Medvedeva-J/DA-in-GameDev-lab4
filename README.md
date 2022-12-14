# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #4 выполнил(а):
- Медведева Юлия Олеговна
- РИ-210940
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы

Ознакомиться с перцептроном

## Задание 1
В новом проекте Unity создала Empty Game Object, навесила на него приложенный к ЛР скрипт.
Обучение перцептрона логическим операциям:
+ OR 
![image](https://user-images.githubusercontent.com/62373163/204086246-877c7292-471d-48cc-a66e-44657970f104.png)
![image](https://user-images.githubusercontent.com/62373163/204086260-8f963e02-b916-4733-89a2-1844a37ff1d2.png)
+ AND
По сравнению с функцией ИЛИ, для обучения нейрона функции И потребовалось большее количество итераций.
![image](https://user-images.githubusercontent.com/62373163/204086882-58c8a9e6-0a99-4341-b422-444dbbcb0aeb.png)
+ NAND
![image](https://user-images.githubusercontent.com/62373163/204086983-47e95880-5f7a-4b44-8cfa-cc2916e964dd.png)
+ XOR
Даже 100000 итераций оказалось недостаточно для обучения этой функции.
![image](https://user-images.githubusercontent.com/62373163/204087288-5b02b077-63bc-4c24-b324-6094b2d9bf3a.png)

## Задание 2 Построить графики зависимости количества эпох от ошибки обучения. Указать от чего зависит необходимое количество эпох обучения

На графике отображена зависимость количества ошибок при обучения от количества используемых при обучении итераций. Как видно на диаграмме, XOR - единственная функция, обучение которой не удалось; для остальных функций потребовалось примерно одинаковое количество итераций.

![image](https://user-images.githubusercontent.com/62373163/204088288-3e88103a-55d2-4df0-a3ca-2bc897a83b81.png)

Вывод: необходимое количество эпох обучения зависит от смещения (bias) и веса (weight).

```cs
double DotProductBias(double[] v1, double[] v2) 
	{
		if (v1 == null || v2 == null)
			return -1;
	 
		if (v1.Length != v2.Length)
			return -1;
	 
		double d = 0;
		for (int x = 0; x < v1.Length; x++)
		{
			d += v1[x] * v2[x];
		}

		d += bias;
	 
		return d;
	}

	double CalcOutput(int i)
	{
		double dp = DotProductBias(weights,ts[i].input);
		if(dp > 0) return(1);
		return (0);
	}
```

## Задание 3 Построить визуальную модель работы перцептрона на сцене Unity
Скрипт для изменения цвета объекта:

```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ChangeColor : MonoBehaviour
{
    private void OnTriggerEnter(Collider other)
    {
        if (other.gameObject.GetComponent<Renderer>().material.color == Color.white && this.gameObject.GetComponent<Renderer>().material.color == Color.white)
        {
            other.gameObject.GetComponent<Renderer>().material.color = Color.white;
            this.gameObject.GetComponent<Renderer>().material.color = Color.white;
        }
        else
        {
            other.gameObject.GetComponent<Renderer>().material.color = Color.black;
            this.gameObject.GetComponent<Renderer>().material.color = Color.black;
        }
    }
}

```
Черные кубы - 1, белые - 0.
При падении кубы меняют цвет в соответствии с результатом (тестируем логическую функцию ИЛИ)
![image](https://user-images.githubusercontent.com/62373163/204088715-712f1059-0dee-4ee5-af65-457b675d9f95.png)
Результат:
![image](https://user-images.githubusercontent.com/62373163/204089030-1fc3d18b-9ad7-4fbd-9471-546e6a228e51.png)


## Выводы
В ходе данной лабораторной работы, я познакомилась с работой перцептрона, изучила процесс обучения логическим операциям, построила графики и изучила зависимость скрорсти обучения от кол-ва эпох, визуализировала работу перцептрона

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |
