---
layout: page
permalink: /blog/
title: Blog
nav: true
nav_order: 1
description:
---

<style>
	header.post-header h1.post-title {
		font-size: clamp(2.8rem, 8vw, 5.4rem);
		font-weight: 700;
		line-height: 0.95;
		letter-spacing: -0.03em;
		margin-bottom: 1.6rem;
	}

	.blog-index {
		max-width: 52rem;
	}

	.blog-posts {
		list-style: none;
		margin: 0;
		padding: 0;
	}

	.blog-divider {
		border: 0;
		border-top: 1px solid var(--global-divider-color);
		margin: 0 0 2rem;
	}

	.blog-posts li {
		border-bottom: 1px solid var(--global-divider-color);
		display: grid;
		gap: 1rem;
		grid-template-columns: minmax(0, 1fr) 4.5rem;
		padding: 1.35rem 0;
	}

	.blog-posts li:first-child {
		padding-top: 0;
	}

	.blog-post-title {
		color: var(--global-text-color);
		display: inline;
		font-size: clamp(1.25rem, 3vw, 1.75rem);
		font-weight: 650;
		line-height: 1.2;
		text-decoration: none;
	}

	.blog-post-title:hover {
		color: var(--global-theme-color);
		text-decoration: none;
	}

	.blog-meta,
	.blog-source,
	.blog-year {
		color: var(--global-text-color-light);
	}

	.blog-meta {
		font-size: 0.92rem;
		line-height: 1.5;
		margin-top: 0.25rem;
	}

	.blog-year {
		align-self: start;
		font-size: 0.95rem;
		justify-self: end;
		line-height: 1.5;
	}

	@media (max-width: 575px) {
		header.post-header h1.post-title {
			margin-bottom: 1.25rem;
		}

		.blog-posts li {
			grid-template-columns: 1fr;
			gap: 0.35rem;
		}

		.blog-year {
			justify-self: start;
			order: -1;
		}
	}
</style>

<div class="blog-index">
	<hr class="blog-divider">

    <ul class="blog-posts" aria-label="All posts">
        <li>
            <div>
                <a class="blog-post-title" href="{{ '/blog/2026/reverse-engineer-asic/' | relative_url }}">Reverse Engineering a Star Battle ASIC</a>
                <div class="blog-meta">September 4, 2026 <span class="blog-source">&nbsp; &middot; &nbsp; this site</span></div>
            </div>
            <div class="blog-year">2026</div>
        </li>
    	<li>
    		<div>
    			<a class="blog-post-title" href="{{ '/blog/2026/training-jepa-world-models/' | relative_url }}">Training JEPA World Models for Robots</a>
    			<div class="blog-meta">18 min read &nbsp; &middot; &nbsp; July 25, 2026 <span class="blog-source">&nbsp; &middot; &nbsp; this site</span></div>
    		</div>
    		<div class="blog-year">2026</div>
    	</li>
    	<li>
    		<div>
    			<a class="blog-post-title" href="https://williamzhang.bearblog.dev/os-and-opt/">Operating Systems and Optimization</a>
    			<div class="blog-meta">May 25, 2026 <span class="blog-source">&nbsp; &middot; &nbsp; Bear Blog</span></div>
    		</div>
    		<div class="blog-year">2026</div>
    	</li>
    	<li>
    		<div>
    			<a class="blog-post-title" href="https://williamzhang.bearblog.dev/c-compiler-2/">Vibing with Compilers: Part 2</a>
    			<div class="blog-meta">May 20, 2026 <span class="blog-source">&nbsp; &middot; &nbsp; Bear Blog</span></div>
    		</div>
    		<div class="blog-year">2026</div>
    	</li>
    	<li>
    		<div>
    			<a class="blog-post-title" href="https://williamzhang.bearblog.dev/c-compiler-1/">Vibing with Compilers: Part 1</a>
    			<div class="blog-meta">February 14, 2026 <span class="blog-source">&nbsp; &middot; &nbsp; Bear Blog</span></div>
    		</div>
    		<div class="blog-year">2026</div>
    	</li>
    </ul>

</div>
