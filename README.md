```golang
package main

import (
	"fmt"
	"math"
)

type Clock struct {
}

func (c Clock) Calculate(hours int, minutes int) float64 {
	hourAngle := c.calculateHourAngle(hours, minutes)
	minuteAngle := c.calculateMinuteAngle(minutes)
	result := math.Abs(minuteAngle - hourAngle)
	if result > 180 {
		return 360 - result
	}

	return result
}

func (c Clock) calculateHourAngle(hours int, minutes int) float64 {
	oneHourAngle := 360/12
	hourMovingForward := oneHourAngle * minutes/60
	currentAngle := hourMovingForward +  360 * hours/12
	return float64(currentAngle)
}

func (c Clock) calculateMinuteAngle(minutes int) float64 {
	currentAngle := 360 *minutes/60
	return float64(currentAngle)
}

func main() {
	c := Clock{}
	angle := c.Calculate(4, 30)

	result := (angle == 45)
	fmt.Print(result)// true
}
```

```python
class Clock:
    def calculate(self, hours: int, minutes: int) -> float:
        hour_angle = self.__calculate_hour_angle(hours, minutes)
        minute_angle = self.__calculate_minute_angle(minutes=minutes)

        result = abs(minute_angle - hour_angle)
        if result > 180:
            return 360 - result

        return result

    def __calculate_hour_angle(self, hours, minutes) -> float:
        one_hour_angle = 360 / 12
        hour_moving_forward = one_hour_angle * minutes / 60
        current_angle = 360 * hours / 12 + hour_moving_forward
        return current_angle

    def __calculate_minute_angle(self, minutes) -> float:
        current_angle = 360 * minutes / 60
        return current_angle


if __name__ == '__main__':
    c = Clock()
    angle = c.calculate(1, 30)

    assert (angle == 130) == True
# 6, 00 -> 180

```