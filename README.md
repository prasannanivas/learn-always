#include<stdio.h>
#include<stdlib.h>
#include<math.h>
int
randomgen (int a, int b)
{
  return rand () % (b);
}

void
main ()
{
  float summ1, summ2, sumbai;
  int x1[50] = { 0 };
  int x2[50] = { 0 };
  float cost;
  float lr = 0.05;
  float y_predict[50] = { 0 };
  float target[50] = { 0 };
  int bias;
  float m1 = 1, m2 = 2, bai = 1;
  for (int i = 0; i < 50; i++)
    {
      x1[i] = randomgen (1, 10);
      x2[i] = randomgen (1, 10);
    }
  int M1, M2;
  printf ("\nEnter M1 : ");
  scanf ("%d", &M1);
  printf ("\nEnter M2 : ");
  scanf ("%d", &M2);
  printf ("\nEnter bias : ");
  scanf ("%d", &bias);
  for (int i = 0; i < 50; i++)
    {
      target[i] = M1 * x1[i] + M2 * x2[i] + bias;
    }
  int prassy = 1500;
  for (int i = 0; i < 50; i++)
    {
      printf ("%d         %d      %d       %f\n", x1[i], x2[i], bias,
	      target[i]);
    }
  while (prassy--)
    {
      cost = 0;
      summ1 = 0;
      summ2 = 0;
      sumbai = 0;
      for (int i = 0; i < 50; i++)
	{
	  y_predict[i] = (m1 * x1[i]) + (m2 * x2[i]) + bai;
	}
      for (int i = 0; i < 50; i++)
	{
	  cost +=
	    (y_predict[i] - target[i]) * (y_predict[i] - target[i]) / 100;
	}
      for (int i = 0; i < 50; i++)
	{
	  summ1 += (y_predict[i] - target[i]) * x1[i];
	  summ2 += (y_predict[i] - target[i]) * x2[i];
	  sumbai += ((y_predict[i] - target[i]));
	}
      m1 = m1 - (lr * summ1) / 100;
      m2 = m2 - (lr * summ2) / 100;
      bai = bai - (lr * sumbai) / 100;
      printf ("\n Cost : %f \n m1 : %f\n m2 : %f\nBias : %f", cost, m1, m2,bai);
  }
  printf("\nDid you enter %f , %f , %f",m1,m2,bai);
}
