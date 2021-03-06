---
permalink: /manual/people
title: "People"
sidebar:
  title: "Manual"
  nav: manual
---

CCBK supports multiple classes of citizens, create a Population ScriptableObject for each one. Different populations may be able to fill different job openings or pay different tax rates.
>plebs, scholars, aristocrats, ...

## Housing

Housing components provide space for a specified number of a defined population. Migrations control how fast new citizens arrive or leave based on their sentiment value.

<div class="mxgraph" style="" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;app.diagrams.net\&quot; modified=\&quot;2021-01-13T18:42:31.947Z\&quot; agent=\&quot;5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Safari/537.36\&quot; etag=\&quot;lwZ9SBzZa1qYL7ixFsRw\&quot; version=\&quot;14.1.9\&quot; type=\&quot;google\&quot;&gt;&lt;diagram id=\&quot;9qOzim73K5z7fP5IoGjb\&quot; name=\&quot;Housing\&quot;&gt;7Vldc5s4FP01fjSD+PZj7Hg33XG73clDk7x0ZBCgViAsRIzz61eAMGCw46Su7XbqBw86iIukc+/RkT3SZ1H+N4NJ+JF6iIw01ctH+u1I0yzbFt8FsKkA3XYqIGDYqyDQAPf4BUlQlWiGPZR2OnJKCcdJF3RpHCOXdzDIGF13u/mUdN+awAD1gHsXkj76BXs8rFDHVBv8DuEgrN8MVHkngnVnCaQh9Oi6BenzkT5jlPLqKspniBRrV69LxD/liTcJmf3VZcbj06fwKR9Xwf56yyPbKTAU83eHfl7c0XvuL14evX8enKc7FD7YY1NOjW/q9UKeWD7ZpIyHNKAxJPMGnTKaxR4qoqqi1fRZUJoIEAjwG+J8I3MBZpwKKOQRkXdRjvlD6/qxCKWYsnWby8hlY1M3Ys42D+1G9ZRm1u3mubJVP+jTmMuRgKJdTbiY5U5+vLK4sl9KM+aiAysqk4VDFiB+oB/YZpCoPEQjJAYtnmOIQI6fu4ODsgaCbb+GZ3EhqR6mfbzit6vsv/lnVfv3ZrUK5wugj7Uq7jMkmXxTKmaPo2IJNAtGgsdpIEY/VQfzYwGXQiQ6nEKCg1hcuyIEYgJ4RoxjUYY38kaEPa9KH5TiF7gs4xWEJBTHvJygOR2Zt3spKwKifEgzZLCmUttk7k/7/uLL6GORVsZErtHRhMhwn4vptGKBelCbLaBYmtr67MSkvp+KzNmleDvMo1g/lJot1j9EEQ6YmB+NBe+kYHzJOnxbq6zQt5KTcVqSciM6ADXJS2bq++KqTJgvkHwX/PeyhhAh+AX96xBzdJ/AsojWYsvZyaM0qXYBH+eFxkx9TMiMEsrKQLrvI8t1BZ5yRr+j1h3PnizV/RU/kD7H1fzeNNHtLrN6zfS62WcsCYWtLabGfqSqB/m1LinmtWK/ScxBV8ztaxNzvS/mg3pqXVLM9SPEnPzGYr5n8Vtirut6p1JPJO3doGfR9cEEGOb1IiZOO9bFKWan9K+s7uuDymsmzrhk3Ru9uneh2FcxL4bgIZchmAqGizpqtvZqlxYVL04yYsFokhG5/f/i0rC/MvZKg6oAoFldd3YaaQCOAiY7tm+imNq5FGFyPU7Afp8VuDYncKwi6GdShEODbCnCHc1SHAd9BZjRKKFxaRF2MqXJA/C6Xd9x5x5Ejj/ozi3XQUu/Jk6+rT6QnNyaG7vW3Opb88mANTfNn8RM36PNf+Tk9efY1XBrqOc7dg2KLegv+xnFdnvUemzd+cWPXcaRYnvR39DMQ/YLx1v79Tv6qsMVKo5cKnDsTpWCk/gqzVIsoxsXKIbzE2zVobzs7K8RIihN/2j4mzTcAjv7s2kr5mVV3L6kir/zEH01lnn/j2JHqPieQ9p5VNzqlfTHxped0hmbyPGMoeJztKVuWedyxsIuveqMh+ruHc5YNJs/RysJbv5h1uf/Aw==&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://viewer.diagrams.net/js/viewer-static.min.js"></script>

One migration script per population is needed which allows different rates of immi-/emigration per population as well as different entry points on the map.

## Employment

Directly sustained by the population is the employment system.
Individual Buildings either always have full access to the employment pool or they send out an EmploymentWalker that checks if any buildings housing the needed population are nearby.  
Employment is mostly used to drive building efficiency. 

<div class="mxgraph" style="" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;app.diagrams.net\&quot; modified=\&quot;2021-01-15T18:08:13.470Z\&quot; agent=\&quot;5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Safari/537.36\&quot; etag=\&quot;i25_663Kt-88mlB70-oi\&quot; version=\&quot;14.2.3\&quot; type=\&quot;google\&quot;&gt;&lt;diagram id=\&quot;SqLUK7N2LWciYIHjsXy-\&quot; name=\&quot;Employment\&quot;&gt;1ZZLj5swEMc/DceNAAObHPPcPbRSpKhqrw6egCWDWeM82E9fOxgIcTZR0na1vSD77/EM/s344aBpdngRuEi/cwLM8V1ycNDM8f3R0FNfLVS1EAbDWkgEJbXkdcKKvoMRXaNuKYGyZyg5Z5IWfTHmeQ6x7GlYCL7vm20460ctcAKWsIoxs9WflMi0Voeh2+mvQJO0iey5ZiTDjbERyhQTvj+R0NxBU8G5rFvZYQpMs2u4TKPlj9X6yQ/it5JUO1LMflVPtbPFPVPaJQjI5d917deud5htDa8lL7YMS8rzseNHTMWbrIVqJbrVwill1QAWfJsT0EFcZbFPqYRVgWM9ulcVpbRUZkz1PNU04UBIOJzl58bivJa4qlTgGUhRqXnGC3LD2o+pUj8wP7rvcu6NjE16km9k7LAps6R13aFUDUPzDrLIIjvPCsarTC/TAvuiKBbK3LOHIvWHi+g/4Y7cC9zdC9yjf8U9uMR9MBh8zNy3h/T+XvhflHnQHK1XmDfH26cgDx8qdfQB9vCrYo9uY2/Px0/hHlncLXKQk7G+RFUvZrgsaXwJFhDrDn0M1Y0KbDQB+obZ9WNewmMiLDnVldQdOs+Ds+N+dMa45FsRg5l3eimeuQoj/5YriUUC0nJ1zFi79MeT+GzfwIJyQWVlJ1Ol6Rteq/dZL4eY0STXCVYpA6EEXftUvYDGZiCjhGgfEwElfcfroz+9kwq9qOMyw4kTzq5tHvM8M5O7R9HNSomubip34KFR1E/An9VIY8I3mxLuzJjqds+52rx7E6P5bw==&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://viewer.diagrams.net/js/viewer-static.min.js"></script>

It is possible to define different groups of employment to specify which buildings get employees first.
>essentials like water should not cease operation because ore mining is using up its employees

CCBK comes with a dialog that allows the user to change employment priorities at runtime.

## Workers

The worker system is not directly liked to populations but will most likely be effected by building employment/efficiency.  
Some buildings need trained workers to function effectively which creates a slightly different kind of production chain.
>farms, monuments, ...

<div class="mxgraph" style="" data-mxgraph="{&quot;highlight&quot;:&quot;#0000ff&quot;,&quot;lightbox&quot;:false,&quot;nav&quot;:true,&quot;edit&quot;:&quot;_blank&quot;,&quot;xml&quot;:&quot;&lt;mxfile host=\&quot;app.diagrams.net\&quot; modified=\&quot;2021-01-13T18:42:09.879Z\&quot; agent=\&quot;5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Safari/537.36\&quot; etag=\&quot;jch2PoGIb0MxzfKCUaui\&quot; version=\&quot;14.1.9\&quot; type=\&quot;google\&quot;&gt;&lt;diagram id=\&quot;Cp6lsMUBnxWaOVh_Lk4D\&quot; name=\&quot;Workers\&quot;&gt;7VnbctowEP0aHpPxBQN+DIYm7ZSGTMgQnjrCXmMnsuUKAaZfXxkkfE1CEihmJi+M9liS5XN2VyvR0K0gvqYo8gbEAdzQFCdu6L2GpnVUnf8mwHoLNI3mFphR39lCagrc+39BgIpAF74D81xHRghmfpQHbRKGYLMchiglq3w3l+D8WyM0E29UUuDeRhhK3ca+wzzxWUam9w34M0++WVXEkwDJzgKYe8ghqwyk9xu6RQlh21YQW4AT7iQvi8GDOQqGd4Dgj28F7o+oH19sJ/v2niG7T6AQsg9PbXh3Vle9mV88T0ZaNB7poaNetMWnsbXkCxxOnzAJZR6ZkRDhfop2KVmEDiSzKtxK+/wkJOKgysEnYGwtfAEtGOGQxwIsnkLss8dMe5JMdWkIqxeLmTfGWhoho+vHrJEZlZjpsI0lx22/L/mogju8waXoNycLasMrBArfYIjOgL3ST9s5DA80IAHwRfJxFDBi/jK/OCRcfrbrl8rKG0LZd6gsFrlEeCHeNCb0GWhDa2G+6O40ac2S1hjhDV50Cox5vCbirzyfwX2ENqSseMbIS4vm0TaIXT9OXKTr+hhbBBO6mUh3XWjZNsfnjJJnyDxx2uZUSRVbAmUQf0CzMsdiFs0UNMhEJjPUKk0LLQF5mYwgsYOror6gysO8ShmLBBEJEwKK4qTxqL4tUEEPB0HHrdSjZXdg6iYjSMhkQlCOJU6znRdHb5XFMSvEMYzPi3O1mjz9Hlzf3k5+jSZT7BjkqidD5pwSY5oLJ3KOEyZGbc/E+IJfHDwxVqqsnrvKyrmobJ5y/9NKmfZ7NtUWXIDXeVHS9CBGXFnOYgTU5ysBmqJDCWn75Fy+Fwp3UGVGFeYxdzy9kFSbmlFKqp2KpKofa8czvsLtc+Gm7xluSrVf/J9o00vRZq1t7NsV1eYmCIeULPkZsU41z7Ei0ny7ytmdPw9d5lRq1Tr3iDx1mdM8h4hsliJySAjmEn5FZPFQ2D51RHZKWpVDdN/T+LFI213uyTzW0S7LpYVaQZt6tMN0+Y6jhrw168dbuTauIW/F24Ea8FaucurHm67Uj7fWGfCmtY38rmCenrf2OfDWqR9vZom3AQkXASRHcAY1qnBOcs9aVe8c6J6Vm+l/Y5tnmT8Y9f4/&lt;/diagram&gt;&lt;/mxfile&gt;&quot;}"></div>
<script type="text/javascript" src="https://viewer.diagrams.net/js/viewer-static.min.js"></script>
