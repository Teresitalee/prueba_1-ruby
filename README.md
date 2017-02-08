# prueba_1-ruby
opcion = 0

while opcion != 4
  puts "\n-----  Menu -----"
  puts " 1. Generar archivo de alumnos"
  puts " 2. Alumnos inasistentes"
  puts " 3. Alumnos aprobados"
  puts " 4. Salir" 
  puts "-----------------" 
  puts "\n\nIngrese opcion valida: "
  opcion = gets.chomp.to_i

  case opcion
  when 1
    system("touch alumnos.txt")
    puts "Se ha creado el archivo alumnos.txt"
    file = File.open("archivo.csv", "r")
    data = file.readlines()

    promedio = 0

    def promedio(nombre, n1, n2, n3, n4, n5)
      file2 = File.open("alumnos.txt", "a")
      promedio = (n1.to_f+n2.to_f+n3.to_f+n4.to_f+n5.to_f)/5
      file2.puts "#{nombre} #{promedio}"
      file2.close
    end

    data.each do |i|
      a = i.split(" ")
        a.each_slice(6) do |alumno|
        promedio(*alumno)
      end
    end
    puts "Se agregaron los alumnos al archivo alumnos.txt"
    file.close

  when 2
    file = File.open("archivo.csv", "r")
    data = file.readlines()

    puts "Inasistencia por alumnos: "
    def inasistencia(alumno)
      suma = 0
      alumno.each_with_index do |v,i|
        if v.to_s.include? "A"
          suma+=1
        end
      end
      puts "#{alumno[0]} #{suma}"
    end

    data.each do |i|
      a = i.split(" ")
        a.each_slice(6) do |alumno|
        inasistencia(alumno)
      end
    end
    file.close

  when 3
    file = File.open("alumnos.txt", "r")
    data = file.readlines()
    puts "Ingrese nota de aprobacion: "
    nota = gets.chomp.to_i

    puts "Alumnos aprobados: "
    def aprobado(alumnos,promedio,nota = 5)
      if promedio.to_i>nota
      puts "#{alumnos} #{promedio}"
    end
    end

    data.each do |i|
      a = i.split(" ")
        a.each_slice(2) do |alumno|
        aprobado(*alumno, nota)
      end
    end

    file.close

  when 4
    puts "ciao..."
  else
    puts "Ingrese una opcion valida:\n"
  end
end

 





