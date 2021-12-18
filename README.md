# Сохраняем информацию в текстовый файл и выгружаем в другое поле
```
   public void buttonSaveClick(View view)
    {
        try
        {
            EditText textBox = (EditText) findViewById(R.id.editTextTextPersonName);
            String text = textBox.getText().toString();
            try {
                file.createNewFile();
            }
            catch (IOException ex)
            {
                Toast.makeText(this, ex.getMessage(), Toast.LENGTH_SHORT).show();
            }
            FileOutputStream fos = new FileOutputStream(file);
            fos.write(text.getBytes());
            fos.close();
            Toast.makeText(this, "Текстовый файл успешно сохранён!", Toast.LENGTH_SHORT).show();
        }
        catch (FileNotFoundException e)
        {
            e.printStackTrace();
            Toast.makeText(this, "Файл не найден!", Toast.LENGTH_SHORT).show();
        } catch (IOException e)
        {
            e.printStackTrace();
            Toast.makeText(this, "Ошибка сохранения файла!", Toast.LENGTH_SHORT).show();
        }
    }

    public void buttonOpenClick(View view)
    {
        try
        {
            FileInputStream fin = new FileInputStream(file);
            byte[] bytes = new byte[fin.available()];
            fin.read(bytes);
            String text = new String(bytes);
            TextView textView = (TextView) findViewById(R.id.textView);
            textView.setText(text);
            fin.close();
        } catch (IOException ex)
        {
            Toast.makeText(this, ex.getMessage(), Toast.LENGTH_SHORT).show();
        }
    }
```
![image](https://user-images.githubusercontent.com/91714397/146625794-250b0b46-d4a2-45a8-a8da-40f802adb2bb.png)
![image](https://user-images.githubusercontent.com/91714397/146625795-7e7c39ab-1985-4726-9969-f3b08da8ecca.png)
