# GEOLOCATION_TRACKER_task5

#pip install geocoder folium

import geocoder
import folium

def get_geolocation(ip):
    location = geocoder.ip(ip)
    return location.latlng

def display_map(location):
    map = folium.Map(location=location, zoom_start=10)
    folium.Marker(location=location, popup="Your Location").add_to(map)
    map.save("map.html")
    print("Map saved as map.html")

def main():
    ip = input("Enter IP address (or press Enter to use your current IP): ")
    if not ip:
        ip = 'me'  # 'me' option will use the current IP address

    try:
        location = get_geolocation(ip)
        print("Your geolocation (latitude, longitude):", location)
        display_map(location)
    except Exception as e:
        print("Error fetching geolocation:", str(e))

if __name__ == "__main__":
    main()
