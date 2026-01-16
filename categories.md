---
layout: page
title: "Topic Library"
permalink: /categories/
---

<div class="max-w-3xl mx-auto px-6 py-20">
    <h1 class="text-4xl font-bold text-blue-900 mb-4">Subject Library</h1>
    <p class="text-slate-600 mb-12">Browse all engineering insights by technical subject.</p>

    <div class="space-y-16">
        {% for category in site.categories %}
            {% capture category_name %}{{ category | first }}{% endcapture %}
            <section id="{{ category_name | slugify }}" class="scroll-mt-20">
                <div class="flex items-center gap-4 mb-6">
                    <h2 class="text-3xl font-bold text-blue-900 uppercase tracking-tighter">
                        {{ category_name }}
                    </h2>
                    <div class="h-1 flex-1 bg-blue-50"></div>
                </div>
                
                <ul class="grid grid-cols-1 gap-4">
                    {% for post in category.last %}
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