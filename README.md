const N = 50;
  const candidates = nearByFreeSpots
    .map(spot => ({
      ...spot,
      distToUser: getDistance(
        userLocation.lat, userLocation.lng,
        spot.coordLat, spot.coordLng
      ),
      distToDest: getDistance(
        destinationLocation.lat, destinationLocation.lng,
        spot.coordLat, spot.coordLng
      )
    }))
    .sort((a, b) => {
      if (value === 'closestToUser')         return a.distToUser - b.distToUser;
      if (value === 'closestToDestination') return a.distToDest - b.distToDest;
      return 0; // for “cheapest” you don’t sort here
    })
    .slice(0, N);
