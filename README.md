# MPU6050-STM32
# MPU6050 Sensor Interface Project
This project demonstrates how to interface with the MPU6050 sensor (a 6-axis motion tracking device with a gyroscope and accelerometer) using STM32F401. The code provided allows you to retrieve data from the sensor using I2C interface.

# main.c

```
/* USER CODE BEGIN 0 */
MPU6050_t MPU6050;

int _write(int fd, char* ptr, int len) {
    HAL_UART_Transmit(&huart2, (uint8_t *) ptr, len, HAL_MAX_DELAY);
    return len;
}
/* USER CODE END 0 */


  /* USER CODE BEGIN 2 */

  while (MPU6050_Init(&hi2c1) == 1);

  /* USER CODE END 2 */
  /* USER CODE BEGIN WHILE */
  while (1)
  {
    /* USER CODE END WHILE */

    /* USER CODE BEGIN 3 */
	  MPU6050_Read_All(&hi2c1, &MPU6050);

	  printf("Ax: %f\n", MPU6050.Ax);
	  printf("Ay: %f\n", MPU6050.Ay);
	  printf("Az: %f\n", MPU6050.Az);

	  printf("Gx: %f\n", MPU6050.Gx);
	  printf("Gy: %f\n", MPU6050.Gy);
	  printf("Gz: %f\n", MPU6050.Gz);

	  printf("x: %f\ny: %f", MPU6050.KalmanAngleX, MPU6050.KalmanAngleY);

	  HAL_Delay (100);

  }
  /* USER CODE END 3 */
}

```
