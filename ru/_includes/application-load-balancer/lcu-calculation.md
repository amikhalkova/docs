Использование балансировщика измеряется в _ресурсных единицах_. Одна ресурсная единица включает в себя:

* 1000 запросов в секунду (RPS);
* 4000 одновременно активных соединений;
* 200 новых соединений в секунду;
* 22 МБ (176 Мбит) трафика в секунду.

Количество ресурсных единиц за час работы балансировщика рассчитывается по показателю с наибольшим потреблением относительно порога. При расчете количество единиц округляется до большего целого значения.

Для каждой зоны доступности количество ресурсных единиц вычисляется отдельно. Минимальное количество единиц в час для одной зоны — 2. Работа балансировщика в зонах, где прием трафика отключен, не тарифицируется.

При расчете количества ресурсных единиц используются максимальные значения показателей за час.