---
layout: page
title: "Methods Index"
permalink: /tags/
---

<div class="max-w-3xl mx-auto px-6 py-20">
    <h1 class="text-4xl font-bold text-blue-900 mb-4">Methods Index</h1>
    <p class="text-slate-600 mb-12">Deconstructing technical mastery through global learning frameworks.</p>

    <div class="space-y-16">
        {% capture tags_string %}{% for tag in site.tags %}{{ tag[0] }}{% unless forloop.last %}|{% endunless %}{% endfor %}{% endcapture %}
        {% assign sorted_tags = tags_string | split: '|' | sort %}

        {% for tag_name in sorted_tags %}
            {% assign posts = site.tags[tag_name] %}
            <section id="{{ tag_name | slugify }}" class="scroll-mt-20">
                <div class="flex items-center gap-4 mb-6">
                    <h2 class="text-3xl font-bold text-blue-900 uppercase tracking-tighter">
                        {{ tag_name | replace: "-", " " }}
                    </h2>
                    <div class="h-1 flex-1 bg-blue-50"></div>
                </div>
                
                <ul class="grid grid-cols-1 gap-4">
                    {% for post in posts %}
                    <li>
                        <a href="{{ post.url }}" class="group block p-4 rounded-xl border border-slate-100 hover:border-orange-200 hover:bg-orange-50 transition">
                            <span class="block text-lg font-semibold text-slate-800 group-hover:text-blue-900">{{ post.title }}</span>
                            <span class="text-xs text-slate-400">{{ post.date | date: "%B %d, %Y" }}</span>
                        </a>
                    </li>
                    {% endfor %}
                </ul>
            </section>
        {% endfor %}
    </div>
</div>