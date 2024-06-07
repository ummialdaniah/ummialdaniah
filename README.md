Model dan Metode CRUD di Python

1. Model:

from sqlalchemy import Column, Integer, String, create_engine
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker

Base = declarative_base()

class Student(Base):
    __tablename__ = 'students'
    id = Column(Integer, primary_key=True)
    name = Column(String)
    address = Column(String)
    gender = Column(String)
    program_of_study = Column(String)
    semester =
Column(Integer)

engine = create_engine('sqlite:///students.db')
Base.metadata.create_all(engine)
Session = sessionmaker(bind=engine)
session = Session()

2. Metode CRUD:

def create_student(name, address, gender, program_of_study, semester):
    new_student = Student(
        name=name,
        address=address,
        gender=gender,
        program_of_study=program_of_study,
        semester=semester
    )
    session.add(new_student)
    session.commit()

def read_student(student_id):
    student = session.query(Student).filter_by(id=student_id).first()
    return student

def update_student(student_id, name=None, address=None, gender=None, program_of_study=None, semester=None):
    student = session.query(Student).filter_by(id=student_id).first()
    if student:
        if name:
            student.name = name
        if address:
            student.address = address
        if gender:
            student.gender = gender
        if program_of_study:
            student.program_of_study = program_of_study
        if semester:

student.semester = semester
        session.commit()
    return student

def delete_student(student_id):
    student = session.query(Student).filter_by(id=student_id).first()
    if student:
        session.delete(student)
        session.commit()

Langkah-langkah untuk Mengunggah ke GitHub

Inisialisasi Repositori:
git init

Tambahkan Berkas ke Staging Area:
git add

Commit Perubahan:
git commit -m "Menambahkan metode CRUD untuk tabel siswa"

Ikuti instruksi untuk menghubungkan repositori lokal Anda ke repositori GitHub

Push ke GitHub:
git remote add origin <URL repositori GitHub Anda>
git branch -M main
git push -u origin main
