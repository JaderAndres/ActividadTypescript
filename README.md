//# ActividadTypescript
//Script con CRUD en Typescript

class Estudiante
{
    id:string = '';
    nombre:string = '';
    apellido:string = '';
    carrera:string = '';
    arrayEstudiantes:Array<any> = []; 
}

interface IEstudiante extends Estudiante
{
    getAll():void;
    getById(codigo:string):void;
    getByName(nombre:string):void;
    create():void;
    update():void;
    delete(id:string):void;
}

class RepositorioEstudiante implements IEstudiante
{
    id: string = '';
    nombre: string = '';
    apellido: string = '';
    carrera: string = '';
    arrayEstudiantes: any[];

    constructor()
    {        
        this.arrayEstudiantes = [];
    }
    
    getAll():void
    {
        //console.log(this.arrayEstudiantes);   

        let datos = 'LISTADO DE ESTUDIANTES:\n';
        for (let i = 0; i < this.arrayEstudiantes.length; i++)
        {
            datos = datos + this.arrayEstudiantes[i].id + " - " + this.arrayEstudiantes[i].nombre + " " + this.arrayEstudiantes[i].apellido + " - " + this.arrayEstudiantes[i].carrera + '\n';
               
        }
        alert(datos);
        console.log(datos);
    }
    getById(id:string): void {
        let resultado = this.arrayEstudiantes.find(item => item.id.toString() == id.trim());        
        if(resultado != undefined)
        {
            //this.arrayEstudiantes[i].nombre + " " + this.arrayEstudiantes[i].apellido + " - " + this.arrayEstudiantes[i].carrera + '\n';
            console.log(resultado);
        }
        else
        {
            console.log("El id '" + id + "' no fue encontrado!");
        }
    }
    getByName(nombre:string): void {
        let resultado = this.arrayEstudiantes.find(item => item.nombre.toString() == nombre.trim());  
        if(resultado != undefined)
        {      
            console.log(resultado);
        }
        else
        {
            console.log("El nombre '" + nombre + "' no fue encontrado!");
        }
    }    
    create(): void {        
        //let estudiante = {id: this.id, nombre:this.nombre, apellido: this.apellido, carrera: this.carrera};
        //this.arrayEstudiantes.push(estudiante);                
        this.arrayEstudiantes.push({id: this.id, nombre:this.nombre, apellido: this.apellido, carrera: this.carrera}); 
        console.log("Estudiante creado exitosamente:");
        console.log(this.arrayEstudiantes);
    }
    update(): void {
        let index = this.arrayEstudiantes.findIndex((obj => obj.id.toString() == this.id));
        this.arrayEstudiantes[index].nombre = this.nombre;
        this.arrayEstudiantes[index].apellido = this.apellido;
        this.arrayEstudiantes[index].carrera = this.carrera;        
        console.log("Estudiante actualizado exitosamente");
        console.log(this.arrayEstudiantes);   
    }
    delete(id:string): void {        
        let index = this.arrayEstudiantes.findIndex((obj => obj.id == id));        
        this.arrayEstudiantes.splice(index, 1);
        console.log("El estudiante ha sido eliminado");
        console.log(this.arrayEstudiantes);           
    }
} 

let objRepoEstudiante = new RepositorioEstudiante();

objRepoEstudiante.id = '71';
objRepoEstudiante.nombre = "Jader";
objRepoEstudiante.apellido = "Gaviria";
objRepoEstudiante.carrera = "Ingeniería de Sistemas"
objRepoEstudiante.create();

objRepoEstudiante.id = '90';
objRepoEstudiante.nombre = "Karen";
objRepoEstudiante.apellido = "Rios";
objRepoEstudiante.carrera = "Veterinaria"
objRepoEstudiante.create();

let menu = 0;
do
{
menu = Number(prompt(" Saludos! \n " +                            
                            "Seleccione su operación para estudiantes : \n " +
                            "\n " +
                            "1. MOSTRAR TODOS \n " +  
                            "2. BUSCAR POR ID \n " +  
                            "3. BUSCAR POR NOMBRE \n " +  
                            "4. CREAR \n " +  
                            "5. ACTUALIZAR \n " +  
                            "6. ELIMINAR \n " +  
                            "7. SALIR \n "                            
                    ));


switch (menu)
{
    case 1:
        //MOSTRAR TODOS
        objRepoEstudiante.getAll();

        break;
    case 2:
        //BUSCAR POR ID
        let id = String(prompt("BUSCAR POR ID:\nDigite el id del estudiante:"));
        objRepoEstudiante.getById(id);

        break;
    case 3:
        //BUSCAR POR NOMBRE
        let nombre = String(prompt("BUSCAR POR NOMBRE:\nDigite el nombre del estudiante:"));
        objRepoEstudiante.getByName(nombre);

        break;
    case 4:
        //CREAR
        let id_e = String(prompt("CREAR:\nDigite el id del estudiante:"));
        objRepoEstudiante.id = id_e;
        let nombre_e = String(prompt("CREAR:\nDigite el nombre del estudiante:"));
        objRepoEstudiante.nombre = nombre_e;
        let apellido_e = String(prompt("CREAR:\nDigite el apellido del estudiante:"));
        objRepoEstudiante.apellido = apellido_e;
        let carrera_e = String(prompt("CREAR:\nDigite la carrera del estudiante:"));
        objRepoEstudiante.carrera = carrera_e;
        
        objRepoEstudiante.create();

        break;
    case 5:
        //ACTUALIZAR
        let id_a = String(prompt("CREAR:\nDigite el id del estudiante que desea actualizar:"));
        objRepoEstudiante.id = id_a;        
        let nombre_a = String(prompt("CREAR:\nDigite el nombre del estudiante:"));
        objRepoEstudiante.nombre = nombre_a;
        let apellido_a = String(prompt("CREAR:\nDigite el apellido del estudiante:"));
        objRepoEstudiante.apellido = apellido_a;
        let carrera_a = String(prompt("CREAR:\nDigite la carrera del estudiante:"));
        objRepoEstudiante.carrera = carrera_a;

        objRepoEstudiante.update();

        break;
    case 6:
        //ELIMINAR
        let id_d = String(prompt("ELIMINAR:\nDigite el id del estudiante que desea eliminar:"));      
        objRepoEstudiante.delete(id_d);

        break;
    case 7:
        //SALIR
        alert("Hasta pronto!");

        break;
    default:
        alert("Opción de acceso no válida. Intente de nuevo!");
        break;

}
} while(menu!=7)
