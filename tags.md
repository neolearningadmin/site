---
layout: page
title: "Learning Methods Index"
permalink: /tags/
---

<div class="max-w-3xl mx-auto px-6 py-20">
    <h1 class="text-4xl font-bold text-blue-900 mb-4">Methods Index</h1>
    <p class="text-slate-600 mb-12">Click a method to see all related technical applications.</p>

    <div class="space-y-12">
        {% capture tags %}
            {% for tag in site.tags %}
                {{ tag[0] }}
            {% endfor %}
        {% endcapture %}
        {% assign sorted_tags = tags | split: ' ' | sort %}

        {% for tag_name in sorted_tags %}
            {% assign posts = site.tags[tag_name] %}
            <section id="{{ tag_name | slugify }}" class="scroll-mt-20">
                <h2 class="text-2xl font-bold text-blue-900 border-b-2 border-orange-200 pb-2 mb-4 uppercase tracking-wide">
                    {{ tag_name | replace: "-", " " }}
                </h2>
                <ul class="space-y-3">
                    {% for post in posts %}
                    <li class="flex items-baseline gap-2">
                        <span class="text-orange-500 text-sm">→</span>
                        <a href="{{ post.url }}" class="text-lg text-slate-700 hover:text-blue-600 hover:underline transition">
                            {{ post.title }}
                        </a>
                        <time class="text-xs text-slate-400 font-mono italic">
                            ({{ post.date | date: "%b %Y" }})
                        </time>
                    </li>
                    {% endfor %}
                </ul>
            </section>
        {% endfor %}
    </div>
</div>