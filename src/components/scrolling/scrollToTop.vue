<template lang="html">
	<div id="top">
		<div id="icon"></div>
	</div>
</template>

<script lang="js">
	export default {
		name: 'scrollToTop',
		props: [],
		mounted() {
			this.insertExternalSource();
		},
		data() {
			return {

			}
		},
		methods: {
			insertExternalSource: function () {

				var elem = document.body || document.documentElement;

				function runScroll() {
					scrollTo(elem, 0, 1000);
				}

				var scrollme;

				scrollme = document.querySelector("#top");
				scrollme.addEventListener("click", runScroll, false)

				function scrollTo(element, to, duration) {

					if (duration <= 0) return;

					var difference = to - element.scrollTop;
					var perTick = difference / duration * 10;

					setTimeout(function () {

						element.scrollTop = element.scrollTop + perTick;

						if (element.scrollTop == to) return;

						scrollTo(element, to, duration - 10);

					}, 10);

				}

				window.onscroll = function () { scrollFunction() };

				function scrollFunction() {

					if (document.body.scrollTop > 20 || document.documentElement.scrollTop > 20) {

						document.getElementById("top").style.display = "block";

					} else {

						document.getElementById("top").style.display = "none";

					}

				}

			}
		},
		computed: {

		}
}
</script>

<style scoped lang="scss">
	#top {
		position: fixed;
		bottom: 2%;
		right: 5%;
		padding: 15px; 
		background-color: #888;
		transition: all 1s ease-in-out;
  }
  #icon {
    padding: 5px; 
    border-top: 4px solid #fff;
    border-left: 4px solid #fff;
    transform: rotate(45deg) translate(15%, 15%);
    transition: all 1s ease-in-out;
  }
</style>
