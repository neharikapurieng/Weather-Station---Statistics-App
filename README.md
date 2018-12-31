# Weather-Station---Statistics-App
//A weather statistics app calculates the minimum, maximum, and average temperature read so far from its subscribed weather station, if any.  
public class StatisticsApp extends WeatherObserver {

	/**
	 * Update the reading of this weather observer. Update the current temperature
	 * and the maximum, minimum, and average accordingly.
	 */
	private WeatherStation wSta;
	private double tempMin, tempAvg, tempMax, tempTotal;
	private int count;

	public void update() {
	
		double temp = wSta.getTemperature();
		if (count == 0) {
			this.tempMax = temp;
			this.tempMin = temp;
			this.tempTotal = temp;
			this.tempAvg = temp;
			this.count = 1;
		} else {
			this.tempTotal += temp;
			this.count++;
			this.tempAvg = this.tempTotal / count;
		}
		if (temp > this.tempMax) {
			this.tempMax = temp;
		}
		if (temp < this.tempMin) {
			this.tempMin = temp;
		}
	}

	/* See the method description in the parent class */
	public WeatherStation getWeatherStation() {
				return wSta;
	}

	/* See the method description in the parent class */
	public void setWeatherStation(WeatherStation ws) {
		this.wSta = ws;
	}

	/**
	 * Get the minimum temperature based on the readings so far.
	 * 
	 * @return minimum temperature based on the readings so far
	 */
	public double getMinTemperature() {
		return this.tempMin;

	}

	/**
	 * Get the maximum temperature based on the readings so far.
	 * 
	 * @return maximum temperature based on the readings so far
	 */
	public double getMaxTemperature() {
		return this.tempMax;
	}

	/**
	 * Get the average temperature based on the readings so far.
	 * 
	 * @return average temperature based on the readings so far
	 */
	public double getAverageTemperature() {
		return this.tempAvg;
	}
}
