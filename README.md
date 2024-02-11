<p align="center">
  <img src="https://repetit.ru/_img/master/logo-desktop.webp" />
</p>

**Заказчик**: сервис Repetit.ru.\
**Задача**. Разработать модель, которая по имеющейся информации о клиенте и заявке будет предсказывать вероятность оплаты заявки клиентом. Заказчик хочет понять, какие заявки будут оплачены, а какие нет, чтобы одни обрабатывать вручную консультантами, а другие нет. Оценка качества модели будет производиться с использованием precision и ROC-AUC.\
\
В начале работы были заполнены пропуски и удалены дубликаты. \
Для каждой заявки было посчитано среднее значение enable_auto_assign(доступен ли репетитор к работе или заблокирован) по всем подходящим по заявке учителям. Таким образом добавился признак mean_enab. Добавился признак count_teach - колличество подходящих на заявку учителей. Признак median_rat - медиана рейтингов подходящих учителей для каждой заявки. И признак mean_same_price - среднее значение по учителям равенства цен у учителя и ученика за занятие (если указанная цена за занятие у учителя и клиента равны, то берётся значение 1, если нет - 0, потом для всех подходящих учителей на заявку берётся среднее).  \
Если хотя бы у одного дубля заявки стоит оплаченно, то ставилось оплаченно для всех соответствующих дублей.\
Признаки, неизвестные на момент подачи заявки удалялись.\
Два текстовых признака были векторизованы с помощью CountVectorizer. \
Самыми важным признакам получился no_teachers_available.\
Метрика ROC-AUC вышла равной 0.73, а precision 0 и 1 соответственно 0.86 и 0.36. Для заказчика важно иметь высокую точность 0, и не так значимо иметь хорошую точность для 1.
