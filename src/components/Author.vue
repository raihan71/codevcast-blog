<template>
	<div class="author">

		<g-image alt="Author image" :src="logo" style="width: 53%" />

		<h1 v-if="showTitle" class="author__site-title">
			{{ $static.metadata.siteName }}
		</h1>

		<p  class="author__intro">
			Code Developer Cast: {{ $static.metadata.siteDescription }}
		</p>

		<p class="author__links">
			<a href="//codevcast.com/" target="_blank">Listen Podcast</a>
			<a href="//network.codevcast.com/" target="_blank">Join Network</a>
		</p>

	</div>
</template>

<static-query>
query {
  metadata {
    siteName,
		siteDescription
  }
}
</static-query>

<script>
import dark from '@/assets/images/dark.png';
import light from '@/assets/images/light.png';

export default {
	data(){
		return {
			logo: light
		}
	},
	props: ['showTitle'],
	mounted() {
		if (window.__theme == 'dark') {
			this.logo = dark
		}
	}
}
</script>

<style lang="scss">
.author {
	margin: 0 auto;
	max-width: 500px;
	text-align: center;
	padding: calc(var(--space) / 2) 0;

	&__image {
		border-radius: 100%;
		width: 90px;
		height: 90px;
		margin-bottom: 1em;
	}

	&__logo {
		width: 50%!important;
	}

	&__intro {
		opacity: .8;
	}

	&__site-title {
		font-size: 1.5em;
	}

	&__links {
		margin-top: -.5em;
		a {
			margin: 0 .5em;
		}
	}
}
</style>
