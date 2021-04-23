## Code Snippet

```javascript
				// L.geoJson(plants, {
				// 	pointToLayer: function (feature, latlng) {
				// 		return L.circleMarker(latlng, commonStyles);
				// 	},
				// 	filter: function (feature) {
				// 		if (feature.properties.fuel_source.Wood) {
				// 			return feature;
				// 		}
				// 	},
				// 	style: function (feature) {
				// 		return {
				// 			color: '#C75912',
				// 			fillColor: '#C75912',
				// 			radius: getRadius(feature.properties.fuel_source.Wood)
				// 		}
				// 	},
				// 	onEachFeature: function (feature, layer) {
				// 		layer.on('mouseover', function () {
				// 			layer.bindPopup(`<strong>${feature.properties.plant_name}</strong>`);
				// 			layer.setStyle({
				// 				fillColor: 'yellow',
				// 				weight: 2
				// 			});
				// 		})
				// 		layer.on('mouseout', function () {
				// 			layer.setStyle({
				// 				fillColor: '#C75912',
				// 				weight: 1
				// 			})
				// 		})
				// 	}
				// }).addTo(map)

				// variable for biomass power plants in US
				// var biomassLayer = L.geoJson(plants, {
				// 	pointToLayer: function (feature, latlng) {
				// 		return L.circleMarker(latlng, commonStyles);
				// 	},
				// 	filter: function (feature) {
				// 		if (feature.properties.fuel_source.Biomass) {
				// 			return feature;
				// 		}
				// 	},
				// 	style: function (feature) {
				// 		return {
				// 			color: '#23F28E',
				// 			fillColor: '#23F28E',
				// 			radius: getRadius(feature.properties.fuel_source.Biomass)
				// 		}
				// 	},
				// 	onEachFeature: function (feature, layer) {
				// 		layer.on('mouseover', function () {
				// 			layer.bindPopup(layer.feature.properties.plant_name);
				// 			layer.setStyle({
				// 				fillColor: 'red',
				// 				weight: 4
				// 			})
				// 		})
				// 		layer.on('mouseout', function () {
				// 			layer.setStyle({
				// 				fillColor: '#23F28E',
				// 				weight: 2,
				// 			})
				// 		})
				// 	}
				// }).addTo(map)
				// onEachFeature: function(feature, layer) {
				// 	layer.on('mouseover', function() {
				// 		layer.setStyle({
				// 			fillColor: 'red',
				// 			weight: 4
				// 		});
				// 	})
				// 	layer.on('mouseout', function() {
				// 		layer.setStyle({
				// 			fillColor: '#23F28E',
				// 			weight: 2




		// for (var i = 0; i < length.plants; i++) {
		// 	var popup = `The name of this power plant is ${plants.features[i].properties.plant_name}`
		// }
		// console.log(popup)

		// variable for wood-burning power plants in US




		// sort the largest circles underneath the smaller ones using JS .sort() method
		// plants.features.sort(function(a, b) {
		// 	return b.properties.capacity_mw - a.properties.capacity_mw;
		// });


		Load power plants as a Leaflet geoJson object:
		L.geoJson(plants, {
					pointToLayer: function (feature, latlng) {
						return L.circleMarker(latlng, {
							color: 'orange',
							weight: 1,
							fillColor: 'yellow',
							fillOpacity: .8, // a second solution to sorting the larger circles under the smaller ones would be to reduce the opacity of the circle's fill but keeping the stroke opacity high
							radius: getRadius(feature.properties.capacity_mw)
						});
					},
					filter: function (feature) {
						if (feature.properties.fuel_source.Hydro ||
							feature.properties.fuel_source.Coal) {
							return feature;
						}
					},
					onEachFeature: function (feature, layer) {
						if (feature.properties.fuel_source.Coal) {
							layer.setStyle({
								fillColor: 'red',
								radius: getRadius(feature.properties.fuel_source.Coal)
							});
						} else if (feature.properties.fuel_source.Hydro) {
							layer.setStyle({
								fillColor: 
								radius: getRadius(feature.properties.fuel_source.Hydro)
							});
						}
					}
				}).addTo(map)
		layer.on('mouseover', function () {
			layer.setStyle({
				fillColor: 'red'
			})
			layer.bindPopup(`The name of this plant is The ${layer.feature.properties.plant_name} plant`)
		});
		layer.on('mouseout', function () {
			layer.setStyle({
				fillColor: 'yellow'
			});
````