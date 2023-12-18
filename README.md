# DATABASE SQRIPT

USE [master]
GO
/****** Object:  Database [DB_DmExam]    Script Date: 15.11.2023 11:49:04 ******/
CREATE DATABASE [DB_DmExam]
 CONTAINMENT = NONE
 ON  PRIMARY 
( NAME = N'DB_DmExam', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\DB_DmExam.mdf' , SIZE = 8192KB , MAXSIZE = UNLIMITED, FILEGROWTH = 65536KB )
 LOG ON 
( NAME = N'DB_DmExam_log', FILENAME = N'C:\Program Files\Microsoft SQL Server\MSSQL16.SQLEXPRESS\MSSQL\DATA\DB_DmExam_log.ldf' , SIZE = 8192KB , MAXSIZE = 2048GB , FILEGROWTH = 65536KB )
 WITH CATALOG_COLLATION = DATABASE_DEFAULT, LEDGER = OFF
GO
ALTER DATABASE [DB_DmExam] SET COMPATIBILITY_LEVEL = 150
GO
IF (1 = FULLTEXTSERVICEPROPERTY('IsFullTextInstalled'))
begin
EXEC [DB_DmExam].[dbo].[sp_fulltext_database] @action = 'enable'
end
GO
ALTER DATABASE [DB_DmExam] SET ANSI_NULL_DEFAULT OFF 
GO
ALTER DATABASE [DB_DmExam] SET ANSI_NULLS OFF 
GO
ALTER DATABASE [DB_DmExam] SET ANSI_PADDING OFF 
GO
ALTER DATABASE [DB_DmExam] SET ANSI_WARNINGS OFF 
GO
ALTER DATABASE [DB_DmExam] SET ARITHABORT OFF 
GO
ALTER DATABASE [DB_DmExam] SET AUTO_CLOSE OFF 
GO
ALTER DATABASE [DB_DmExam] SET AUTO_SHRINK OFF 
GO
ALTER DATABASE [DB_DmExam] SET AUTO_UPDATE_STATISTICS ON 
GO
ALTER DATABASE [DB_DmExam] SET CURSOR_CLOSE_ON_COMMIT OFF 
GO
ALTER DATABASE [DB_DmExam] SET CURSOR_DEFAULT  GLOBAL 
GO
ALTER DATABASE [DB_DmExam] SET CONCAT_NULL_YIELDS_NULL OFF 
GO
ALTER DATABASE [DB_DmExam] SET NUMERIC_ROUNDABORT OFF 
GO
ALTER DATABASE [DB_DmExam] SET QUOTED_IDENTIFIER OFF 
GO
ALTER DATABASE [DB_DmExam] SET RECURSIVE_TRIGGERS OFF 
GO
ALTER DATABASE [DB_DmExam] SET  DISABLE_BROKER 
GO
ALTER DATABASE [DB_DmExam] SET AUTO_UPDATE_STATISTICS_ASYNC OFF 
GO
ALTER DATABASE [DB_DmExam] SET DATE_CORRELATION_OPTIMIZATION OFF 
GO
ALTER DATABASE [DB_DmExam] SET TRUSTWORTHY OFF 
GO
ALTER DATABASE [DB_DmExam] SET ALLOW_SNAPSHOT_ISOLATION OFF 
GO
ALTER DATABASE [DB_DmExam] SET PARAMETERIZATION SIMPLE 
GO
ALTER DATABASE [DB_DmExam] SET READ_COMMITTED_SNAPSHOT OFF 
GO
ALTER DATABASE [DB_DmExam] SET HONOR_BROKER_PRIORITY OFF 
GO
ALTER DATABASE [DB_DmExam] SET RECOVERY SIMPLE 
GO
ALTER DATABASE [DB_DmExam] SET  MULTI_USER 
GO
ALTER DATABASE [DB_DmExam] SET PAGE_VERIFY CHECKSUM  
GO
ALTER DATABASE [DB_DmExam] SET DB_CHAINING OFF 
GO
ALTER DATABASE [DB_DmExam] SET FILESTREAM( NON_TRANSACTED_ACCESS = OFF ) 
GO
ALTER DATABASE [DB_DmExam] SET TARGET_RECOVERY_TIME = 60 SECONDS 
GO
ALTER DATABASE [DB_DmExam] SET DELAYED_DURABILITY = DISABLED 
GO
ALTER DATABASE [DB_DmExam] SET ACCELERATED_DATABASE_RECOVERY = OFF  
GO
ALTER DATABASE [DB_DmExam] SET QUERY_STORE = OFF
GO
USE [DB_DmExam]
GO
/****** Object:  Table [dbo].[EquipmentTypes]    Script Date: 15.11.2023 11:49:04 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[EquipmentTypes](
	[ID] [int] IDENTITY(1,1) NOT NULL,
	[EqimentType] [varchar](50) NOT NULL,
 CONSTRAINT [PK_EquipmentTypes] PRIMARY KEY CLUSTERED 
(
	[ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Orders]    Script Date: 15.11.2023 11:49:04 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Orders](
	[ID] [int] IDENTITY(1,1) NOT NULL,
	[ID_Client] [int] NOT NULL,
	[ID_TypeEquipment] [int] NULL,
	[ID_TypeProblem] [int] NOT NULL,
	[ID_Technician] [int] NOT NULL,
	[ID_Manager] [int] NULL,
	[ID_Status] [int] NOT NULL,
	[DateOrderOpen] [date] NOT NULL,
	[DateOrderClose] [date] NULL,
	[Comment] [varchar](200) NULL,
	[Photo] [varchar](50) NULL,
 CONSTRAINT [PK_Orders] PRIMARY KEY CLUSTERED 
(
	[ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[ProblemTypes]    Script Date: 15.11.2023 11:49:04 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[ProblemTypes](
	[ID] [int] IDENTITY(1,1) NOT NULL,
	[ProblemType] [varchar](50) NOT NULL,
	[Description] [varchar](100) NULL,
 CONSTRAINT [PK_ProblemTypes] PRIMARY KEY CLUSTERED 
(
	[ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Roles]    Script Date: 15.11.2023 11:49:04 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Roles](
	[ID] [int] IDENTITY(1,1) NOT NULL,
	[RoleName] [varchar](50) NOT NULL,
 CONSTRAINT [PK_Roles] PRIMARY KEY CLUSTERED 
(
	[ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Statuses]    Script Date: 15.11.2023 11:49:04 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Statuses](
	[ID] [int] IDENTITY(1,1) NOT NULL,
	[StatusName] [varchar](50) NOT NULL,
 CONSTRAINT [PK_Statuses] PRIMARY KEY CLUSTERED 
(
	[ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Technicians]    Script Date: 15.11.2023 11:49:04 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Technicians](
	[ID] [int] IDENTITY(1,1) NOT NULL,
	[ID_user] [int] NOT NULL,
	[ID_TypeEquipment_1] [int] NULL,
	[ID_TypeEquipment_2] [int] NULL,
	[ID_TypeEquipment_3] [int] NULL,
	[OtherSkills] [varchar](50) NULL,
	[ProfileLink] [varchar](50) NULL,
 CONSTRAINT [PK_Technicians] PRIMARY KEY CLUSTERED 
(
	[ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
/****** Object:  Table [dbo].[Users]    Script Date: 15.11.2023 11:49:04 ******/
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO
CREATE TABLE [dbo].[Users](
	[ID] [int] IDENTITY(1,1) NOT NULL,
	[Login] [varchar](50) NOT NULL,
	[Password] [varchar](50) NOT NULL,
	[FirstName] [varchar](50) NOT NULL,
	[LastName] [varchar](50) NOT NULL,
	[Nikname] [varchar](50) NOT NULL,
	[Mail] [varchar](100) NOT NULL,
	[Phone] [varchar](12) NOT NULL,
	[RegisterDate] [datetime] NOT NULL,
	[ID_role] [int] NOT NULL,
 CONSTRAINT [PK_Users] PRIMARY KEY CLUSTERED 
(
	[ID] ASC
)WITH (PAD_INDEX = OFF, STATISTICS_NORECOMPUTE = OFF, IGNORE_DUP_KEY = OFF, ALLOW_ROW_LOCKS = ON, ALLOW_PAGE_LOCKS = ON, OPTIMIZE_FOR_SEQUENTIAL_KEY = OFF) ON [PRIMARY]
) ON [PRIMARY]
GO
SET IDENTITY_INSERT [dbo].[EquipmentTypes] ON 

INSERT [dbo].[EquipmentTypes] ([ID], [EqimentType]) VALUES (1, N'Смартфон')
INSERT [dbo].[EquipmentTypes] ([ID], [EqimentType]) VALUES (2, N'Планшет')
INSERT [dbo].[EquipmentTypes] ([ID], [EqimentType]) VALUES (3, N'Ноутбук')
INSERT [dbo].[EquipmentTypes] ([ID], [EqimentType]) VALUES (4, N'Принткр')
INSERT [dbo].[EquipmentTypes] ([ID], [EqimentType]) VALUES (5, N'Сканер')
INSERT [dbo].[EquipmentTypes] ([ID], [EqimentType]) VALUES (6, N'Мышка')
INSERT [dbo].[EquipmentTypes] ([ID], [EqimentType]) VALUES (7, N'Клавиатура')
INSERT [dbo].[EquipmentTypes] ([ID], [EqimentType]) VALUES (8, N'Монирор')
SET IDENTITY_INSERT [dbo].[EquipmentTypes] OFF
GO
SET IDENTITY_INSERT [dbo].[Orders] ON 

INSERT [dbo].[Orders] ([ID], [ID_Client], [ID_TypeEquipment], [ID_TypeProblem], [ID_Technician], [ID_Manager], [ID_Status], [DateOrderOpen], [DateOrderClose], [Comment], [Photo]) VALUES (15, 4, 1, 1, 1, NULL, 1, CAST(N'2023-11-15' AS Date), NULL, N'', NULL)
INSERT [dbo].[Orders] ([ID], [ID_Client], [ID_TypeEquipment], [ID_TypeProblem], [ID_Technician], [ID_Manager], [ID_Status], [DateOrderOpen], [DateOrderClose], [Comment], [Photo]) VALUES (16, 4, 2, 1, 1, NULL, 1, CAST(N'2023-11-15' AS Date), NULL, N'', NULL)
INSERT [dbo].[Orders] ([ID], [ID_Client], [ID_TypeEquipment], [ID_TypeProblem], [ID_Technician], [ID_Manager], [ID_Status], [DateOrderOpen], [DateOrderClose], [Comment], [Photo]) VALUES (17, 1002, 1, 1, 1, NULL, 2, CAST(N'2023-11-15' AS Date), NULL, N'', NULL)
SET IDENTITY_INSERT [dbo].[Orders] OFF
GO
SET IDENTITY_INSERT [dbo].[ProblemTypes] ON 

INSERT [dbo].[ProblemTypes] ([ID], [ProblemType], [Description]) VALUES (1, N'Поломка электроники', N'Физическая поломка эелектроники')
INSERT [dbo].[ProblemTypes] ([ID], [ProblemType], [Description]) VALUES (2, N'Программная поломка', N'поломка ОП')
INSERT [dbo].[ProblemTypes] ([ID], [ProblemType], [Description]) VALUES (3, N'Визуальная поломка', N'Поломка корпуса')
SET IDENTITY_INSERT [dbo].[ProblemTypes] OFF
GO
SET IDENTITY_INSERT [dbo].[Roles] ON 

INSERT [dbo].[Roles] ([ID], [RoleName]) VALUES (1, N'Admin')
INSERT [dbo].[Roles] ([ID], [RoleName]) VALUES (2, N'Manager')
INSERT [dbo].[Roles] ([ID], [RoleName]) VALUES (3, N'Master')
INSERT [dbo].[Roles] ([ID], [RoleName]) VALUES (4, N'Client')
SET IDENTITY_INSERT [dbo].[Roles] OFF
GO
SET IDENTITY_INSERT [dbo].[Statuses] ON 

INSERT [dbo].[Statuses] ([ID], [StatusName]) VALUES (1, N'Выполняеться')
INSERT [dbo].[Statuses] ([ID], [StatusName]) VALUES (2, N'Заморожен')
INSERT [dbo].[Statuses] ([ID], [StatusName]) VALUES (3, N'Завершон')
SET IDENTITY_INSERT [dbo].[Statuses] OFF
GO
SET IDENTITY_INSERT [dbo].[Technicians] ON 

INSERT [dbo].[Technicians] ([ID], [ID_user], [ID_TypeEquipment_1], [ID_TypeEquipment_2], [ID_TypeEquipment_3], [OtherSkills], [ProfileLink]) VALUES (1, 3, 1, 2, 3, NULL, NULL)
INSERT [dbo].[Technicians] ([ID], [ID_user], [ID_TypeEquipment_1], [ID_TypeEquipment_2], [ID_TypeEquipment_3], [OtherSkills], [ProfileLink]) VALUES (2, 1009, 3, 4, 1, NULL, NULL)
INSERT [dbo].[Technicians] ([ID], [ID_user], [ID_TypeEquipment_1], [ID_TypeEquipment_2], [ID_TypeEquipment_3], [OtherSkills], [ProfileLink]) VALUES (3, 1010, 2, 6, NULL, NULL, NULL)
SET IDENTITY_INSERT [dbo].[Technicians] OFF
GO
SET IDENTITY_INSERT [dbo].[Users] ON 

INSERT [dbo].[Users] ([ID], [Login], [Password], [FirstName], [LastName], [Nikname], [Mail], [Phone], [RegisterDate], [ID_role]) VALUES (1, N'ilya', N'1234', N'Илья', N'Куликов', N'ilya34', N'нет', N'нет', CAST(N'2004-04-01T00:00:00.000' AS DateTime), 1)
INSERT [dbo].[Users] ([ID], [Login], [Password], [FirstName], [LastName], [Nikname], [Mail], [Phone], [RegisterDate], [ID_role]) VALUES (2, N'dima', N'1234', N'Дмитрий', N'Борода', N'DimaKrut', N'нет', N'нет', CAST(N'2005-03-01T00:00:00.000' AS DateTime), 2)
INSERT [dbo].[Users] ([ID], [Login], [Password], [FirstName], [LastName], [Nikname], [Mail], [Phone], [RegisterDate], [ID_role]) VALUES (3, N'igor', N'1234', N'Игорь', N'Якорь', N'igorMaster', N'нет', N'нет', CAST(N'2020-12-02T00:00:00.000' AS DateTime), 3)
INSERT [dbo].[Users] ([ID], [Login], [Password], [FirstName], [LastName], [Nikname], [Mail], [Phone], [RegisterDate], [ID_role]) VALUES (4, N'jna', N'1234', N'Яна', N'Костыль', N'jnaClient', N'нет', N'нет', CAST(N'2023-09-01T00:00:00.000' AS DateTime), 4)
INSERT [dbo].[Users] ([ID], [Login], [Password], [FirstName], [LastName], [Nikname], [Mail], [Phone], [RegisterDate], [ID_role]) VALUES (1002, N'anna', N'1234', N'Анна', N'Рубёвая', N'AnnClient', N'нет', N'нет', CAST(N'2023-11-11T00:00:00.000' AS DateTime), 4)
INSERT [dbo].[Users] ([ID], [Login], [Password], [FirstName], [LastName], [Nikname], [Mail], [Phone], [RegisterDate], [ID_role]) VALUES (1003, N'lida', N'1234', N'Лида', N'Разная', N'lidaClient', N'нет', N'нет', CAST(N'2023-11-11T00:00:00.000' AS DateTime), 4)
INSERT [dbo].[Users] ([ID], [Login], [Password], [FirstName], [LastName], [Nikname], [Mail], [Phone], [RegisterDate], [ID_role]) VALUES (1004, N'maria', N'1234', N'Мария', N'Безмолвная', N'mariaClient', N'нет', N'нет', CAST(N'2023-11-11T00:00:00.000' AS DateTime), 4)
INSERT [dbo].[Users] ([ID], [Login], [Password], [FirstName], [LastName], [Nikname], [Mail], [Phone], [RegisterDate], [ID_role]) VALUES (1006, N'roma', N'1234', N'Роман', N'Белый', N'romaClient', N'нет', N'нет', CAST(N'2023-11-11T00:00:00.000' AS DateTime), 4)
INSERT [dbo].[Users] ([ID], [Login], [Password], [FirstName], [LastName], [Nikname], [Mail], [Phone], [RegisterDate], [ID_role]) VALUES (1007, N'danil', N'1234', N'Дниил', N'Криворуков', N'danilClient', N'нет', N'нет', CAST(N'2023-11-11T00:00:00.000' AS DateTime), 4)
INSERT [dbo].[Users] ([ID], [Login], [Password], [FirstName], [LastName], [Nikname], [Mail], [Phone], [RegisterDate], [ID_role]) VALUES (1008, N'rita', N'1234', N'Рита', N'Грязнева', N'ritaClient', N'нет', N'нет', CAST(N'2023-11-11T00:00:00.000' AS DateTime), 4)
INSERT [dbo].[Users] ([ID], [Login], [Password], [FirstName], [LastName], [Nikname], [Mail], [Phone], [RegisterDate], [ID_role]) VALUES (1009, N'zoy', N'1234', N'Зоя', N'Машина', N'zoyMaster', N'нет', N'нет', CAST(N'2002-03-01T00:00:00.000' AS DateTime), 3)
INSERT [dbo].[Users] ([ID], [Login], [Password], [FirstName], [LastName], [Nikname], [Mail], [Phone], [RegisterDate], [ID_role]) VALUES (1010, N'gena', N'1234', N'Генадий', N'Скоба', N'genaMaster', N'нет', N'нет', CAST(N'2023-04-01T00:00:00.000' AS DateTime), 3)
SET IDENTITY_INSERT [dbo].[Users] OFF
GO
ALTER TABLE [dbo].[Orders]  WITH CHECK ADD  CONSTRAINT [FK_Orders_EquipmentTypes] FOREIGN KEY([ID_TypeEquipment])
REFERENCES [dbo].[EquipmentTypes] ([ID])
GO
ALTER TABLE [dbo].[Orders] CHECK CONSTRAINT [FK_Orders_EquipmentTypes]
GO
ALTER TABLE [dbo].[Orders]  WITH CHECK ADD  CONSTRAINT [FK_Orders_ProblemTypes] FOREIGN KEY([ID_TypeProblem])
REFERENCES [dbo].[ProblemTypes] ([ID])
GO
ALTER TABLE [dbo].[Orders] CHECK CONSTRAINT [FK_Orders_ProblemTypes]
GO
ALTER TABLE [dbo].[Orders]  WITH CHECK ADD  CONSTRAINT [FK_Orders_Statuses] FOREIGN KEY([ID_Status])
REFERENCES [dbo].[Statuses] ([ID])
GO
ALTER TABLE [dbo].[Orders] CHECK CONSTRAINT [FK_Orders_Statuses]
GO
ALTER TABLE [dbo].[Orders]  WITH CHECK ADD  CONSTRAINT [FK_Orders_Technicians] FOREIGN KEY([ID_Technician])
REFERENCES [dbo].[Technicians] ([ID])
GO
ALTER TABLE [dbo].[Orders] CHECK CONSTRAINT [FK_Orders_Technicians]
GO
ALTER TABLE [dbo].[Orders]  WITH CHECK ADD  CONSTRAINT [FK_Orders_Users] FOREIGN KEY([ID_Client])
REFERENCES [dbo].[Users] ([ID])
GO
ALTER TABLE [dbo].[Orders] CHECK CONSTRAINT [FK_Orders_Users]
GO
ALTER TABLE [dbo].[Technicians]  WITH CHECK ADD  CONSTRAINT [FK_Technicians_EquipmentTypes] FOREIGN KEY([ID_TypeEquipment_1])
REFERENCES [dbo].[EquipmentTypes] ([ID])
GO
ALTER TABLE [dbo].[Technicians] CHECK CONSTRAINT [FK_Technicians_EquipmentTypes]
GO
ALTER TABLE [dbo].[Technicians]  WITH CHECK ADD  CONSTRAINT [FK_Technicians_EquipmentTypes1] FOREIGN KEY([ID_TypeEquipment_2])
REFERENCES [dbo].[EquipmentTypes] ([ID])
GO
ALTER TABLE [dbo].[Technicians] CHECK CONSTRAINT [FK_Technicians_EquipmentTypes1]
GO
ALTER TABLE [dbo].[Technicians]  WITH CHECK ADD  CONSTRAINT [FK_Technicians_EquipmentTypes2] FOREIGN KEY([ID_TypeEquipment_3])
REFERENCES [dbo].[EquipmentTypes] ([ID])
GO
ALTER TABLE [dbo].[Technicians] CHECK CONSTRAINT [FK_Technicians_EquipmentTypes2]
GO
ALTER TABLE [dbo].[Technicians]  WITH CHECK ADD  CONSTRAINT [FK_Technicians_Users] FOREIGN KEY([ID_user])
REFERENCES [dbo].[Users] ([ID])
GO
ALTER TABLE [dbo].[Technicians] CHECK CONSTRAINT [FK_Technicians_Users]
GO
ALTER TABLE [dbo].[Users]  WITH CHECK ADD  CONSTRAINT [FK_Users_Roles] FOREIGN KEY([ID_role])
REFERENCES [dbo].[Roles] ([ID])
GO
ALTER TABLE [dbo].[Users] CHECK CONSTRAINT [FK_Users_Roles]
GO
USE [master]
GO
ALTER DATABASE [DB_DmExam] SET  READ_WRITE 
GO
