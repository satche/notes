# PHP

_A set of html good practices for accessibility and semantic_

## Microdata

[https://schema.org]()

_Improve referencement by define schema object in html tags_

```html
<div itemscope itemtype="https://schema.org/Movie">
	<h1 itemprop="name">Avatar</h1>
	<div itemprop="director" itemscope itemtype="https://schema.org/Person">
		<span itemprop="name">James Cameron</span>
		<span itemprop="birthDate">August 16, 1954</span>
	</div>
	<span itemprop="genre">Science fiction</span>
</div>
```
