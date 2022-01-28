<template>
	<article class="card">
		<!--Calling data for the name of the place where earthquake occured-->
		<h1 class="card__title">{{ earthquake.properties.place }}</h1>
		<!--Calling mangnitude data for the earthquake-->
		<h2 class="card__copy"><strong>Magnitude:</strong> {{ earthquake.properties.mag }} </h2>
		<!--Calling depth data for the earthquake-->
		<h2 class="card__copy"><strong>Depth of earthquake:</strong> {{ earthquake.geometry.coordinates[2] }} km</h2>
		<!--Calling url to show more details of the earthquake-->
		<h2 class="card__copy"><strong>USGS link for more details:</strong> <a v-bind:href= "earthquake.properties.url" target="_blank"> {{earthquake.properties.title}} </a> </h2>
	</article>
</template>

<script>
export default {
	// Property validation for the data
	props: {
		earthquake: {
			typemain: {
				type: String
			},
			metadata: {
				generated: {
					type: Number
				},
				url: {
					type: String
				},
				title: {
					type: String
				},
				api: {
					type: String
				},
				count: {
					type: Number
				},
				status: {
					type: Number
				},
				type: Object
			},
			features: {
				typefeature: {
					type: String
				},
				properties: {
					mag: {
						type: Number
					},
					place: {
						type: String
					},
					time: {
						type: Number
					},
					updated: {
						type: Number
					},
					tz: {
						type: Number
					},
					url: {
						type: String
					},
					detail: {
						type: String
					},
					felt: {
						type: Number
					},
					cdi: {
						type: Number
					},
					mmi: {
						type: Number
					},
					alert: {
						type: String
					},
					status: {
						type: String
					},
					tsunami: {
						type: Number
					},
					sig: {
						type: Number
					},
					net: {
						type: String
					},
					code: {
						type: String
					},
					ids: {
						type: String
					},
					sources: {
						type: String
					},
					types: {
						type: String
					},
					nst: {
						type: Number
					},
					dmin: {
						type: Number
					},
					rms: {
						type: Number
					},
					gap: {
						type: Number
					},
					magtype: {
						type: String
					},
					typeprop: {
						type: String
					},
					title: {
						type: String
					},
					type: Object
				},
				geometry: {
					typegeo: {
						type: String
					},
					coordinates: {
						longitude: {
							type: Number
						},
						latitude: {
							type: Number
						},
						depth: {
							type: Number
						},
						type: Array
					},
					type: Object
				},
				id: {
					type: String
				},
				type: Array
			},
			bbox: {
				minLongitude: {
					type: Number
				},
				minLatitude: {
					type: Number
				},
				minDepth: {
					type: Number
				},
				maxLongitude: {
					type: Number
				},
				maxLatitude: {
					type: Number
				},
				maxDepth: {
					type: Number
				},
				type: Array
			},
			type: Object
		}
	}
}
</script>

<style lang="scss" scoped>

// Importing partials here
@import '@/assets/styles/_base.normalize.scss';
@import '@/assets/styles/_components.content.scss';
@import '@/assets/styles/_settings.responsive.scss';
@import '@/assets/styles/_settings.variables.scss';

.card {
	margin-bottom: 1rem;
	border: 2px solid $gray;
	padding: 1.5rem;
	width: 100%;
	min-height: 200px;
	&__title {
		font-size: 2em;
		margin-bottom: 1rem;
		margin-top: 0;
		font-weight: 400;
		//changed font size for small screen
		@include media-query("mobile") {
			font-size: 1.4em;
		}
	}
	&__copy {
		// Added font styling for h2 tag
		text-transform: capitalize;
		font-size: $font-size;
		font-weight: 100;
		//changed font size for small screen
		@include media-query("mobile") {
			font-size: 1rem;
		}
		// Added style for the url
		a {
			font-style: italic;
			text-decoration: none;
			&:hover, &:visited {
				color: $gray;
			}
		}
	}
	// Added style for strong tag
	strong {
		font-weight: 400;
	}
}
</style>
