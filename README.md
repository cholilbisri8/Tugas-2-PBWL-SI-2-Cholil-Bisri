# Tugas-2-PBWL-SI-2-Cholil-Bisri
Tugas PBWL SI-2

-- phpMyAdmin SQL Dump
-- version 5.2.0
-- https://www.phpmyadmin.net/
--
-- Host: 127.0.0.1
-- Waktu pembuatan: 20 Jun 2023 pada 07.22
-- Versi server: 10.4.24-MariaDB
-- Versi PHP: 8.1.6

SET SQL_MODE = "NO_AUTO_VALUE_ON_ZERO";
START TRANSACTION;
SET time_zone = "+00:00";


/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;

--
-- Database: `database`
--

-- --------------------------------------------------------

--
-- Struktur dari tabel `tb_golongan`
--

CREATE TABLE `tb_golongan` (
  `gol_id` int(11) NOT NULL,
  `gol_kode` varchar(10) DEFAULT NULL,
  `gol_nama` varchar(50) DEFAULT NULL,
  `created_at` timestamp NOT NULL DEFAULT current_timestamp(),
  `updated_at` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data untuk tabel `tb_golongan`
--

INSERT INTO `tb_golongan` (`gol_id`, `gol_kode`, `gol_nama`, `created_at`, `updated_at`) VALUES
(1, '01', 'Rendah', '2023-06-20 05:03:11', NULL),
(2, '02', 'Menengah', '2023-06-20 05:07:48', NULL),
(4, '03', 'Atas', '2023-06-20 05:08:23', NULL);

-- --------------------------------------------------------

--
-- Struktur dari tabel `tb_pelanggan`
--

CREATE TABLE `tb_pelanggan` (
  `pel_id` int(11) NOT NULL,
  `pel_id_gol` int(3) NOT NULL,
  `pel_no` varchar(20) DEFAULT NULL,
  `pel_nama` varchar(50) DEFAULT NULL,
  `pel_alamat` text DEFAULT NULL,
  `pel_hp` varchar(20) DEFAULT NULL,
  `pel_ktp` varchar(50) DEFAULT NULL,
  `pel_seri` varchar(50) DEFAULT NULL,
  `pel_meteran` int(11) DEFAULT NULL,
  `pel_aktif` enum('Y','N') DEFAULT NULL,
  `pel_id_user` int(11) DEFAULT NULL,
  `created_at` timestamp NOT NULL DEFAULT current_timestamp(),
  `updated_at` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data untuk tabel `tb_pelanggan`
--

INSERT INTO `tb_pelanggan` (`pel_id`, `pel_id_gol`, `pel_no`, `pel_nama`, `pel_alamat`, `pel_hp`, `pel_ktp`, `pel_seri`, `pel_meteran`, `pel_aktif`, `pel_id_user`, `created_at`, `updated_at`) VALUES
(1, 1, '01', 'Reza', 'Desa Sei Merah', '081263798735', '1234567890', '00112233', 987654321, '', 1, '2023-06-20 05:04:40', NULL),
(2, 2, '2', 'Asnawi', 'Makasar', '089676562542', '09876543221', '99887766', 778757252, '', 3, '2023-06-20 05:09:33', NULL),
(3, 4, '3', 'Messi', 'Argentina', '087862544252', '725354362722', '98262672', 2147483647, '', 2, '2023-06-20 05:10:30', NULL);

-- --------------------------------------------------------

--
-- Struktur dari tabel `tb_users`
--

CREATE TABLE `tb_users` (
  `user_id` int(11) NOT NULL,
  `user_email` varchar(50) NOT NULL,
  `user_password` varchar(100) NOT NULL,
  `user_nama` varchar(100) DEFAULT NULL,
  `user_alamat` text DEFAULT NULL,
  `user_hp` varchar(25) DEFAULT NULL,
  `user_pos` varchar(5) DEFAULT NULL,
  `user_role` tinyint(2) DEFAULT NULL,
  `user_aktif` tinyint(2) DEFAULT NULL,
  `created_at` timestamp NOT NULL DEFAULT current_timestamp(),
  `updated_at` datetime DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

--
-- Dumping data untuk tabel `tb_users`
--

INSERT INTO `tb_users` (`user_id`, `user_email`, `user_password`, `user_nama`, `user_alamat`, `user_hp`, `user_pos`, `user_role`, `user_aktif`, `created_at`, `updated_at`) VALUES
(1, 'cholilbisri8@gmail.com', '15312', 'Cholil Bisri', 'Jl. Sidomulyo', '087819236030', '20371', 0, 1, '2023-06-20 04:56:48', NULL),
(2, 'muhammadwahyu12@gmail.com', '24635', 'Muhammad Wahyu', 'Jl. Pernah Ada', '083187654542', '20371', 0, 2, '2023-06-20 05:05:51', NULL),
(3, 'sitisarah3@gmail.com', '90765', 'Garnacho', 'Jl. Setia Negara', '08124644562', '20371', 0, 3, '2023-06-20 05:07:02', NULL);

--
-- Indexes for dumped tables
--

--
-- Indeks untuk tabel `tb_golongan`
--
ALTER TABLE `tb_golongan`
  ADD PRIMARY KEY (`gol_id`),
  ADD UNIQUE KEY `gol_kode` (`gol_kode`);

--
-- Indeks untuk tabel `tb_pelanggan`
--
ALTER TABLE `tb_pelanggan`
  ADD PRIMARY KEY (`pel_id`),
  ADD UNIQUE KEY `pel_no` (`pel_no`),
  ADD KEY `pel_id_user` (`pel_id_user`),
  ADD KEY `pel_id_gol` (`pel_id_gol`);

--
-- Indeks untuk tabel `tb_users`
--
ALTER TABLE `tb_users`
  ADD PRIMARY KEY (`user_id`),
  ADD UNIQUE KEY `user_email` (`user_email`);

--
-- AUTO_INCREMENT untuk tabel yang dibuang
--

--
-- AUTO_INCREMENT untuk tabel `tb_golongan`
--
ALTER TABLE `tb_golongan`
  MODIFY `gol_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=5;

--
-- AUTO_INCREMENT untuk tabel `tb_pelanggan`
--
ALTER TABLE `tb_pelanggan`
  MODIFY `pel_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=4;

--
-- AUTO_INCREMENT untuk tabel `tb_users`
--
ALTER TABLE `tb_users`
  MODIFY `user_id` int(11) NOT NULL AUTO_INCREMENT, AUTO_INCREMENT=4;

--
-- Ketidakleluasaan untuk tabel pelimpahan (Dumped Tables)
--

--
-- Ketidakleluasaan untuk tabel `tb_pelanggan`
--
ALTER TABLE `tb_pelanggan`
  ADD CONSTRAINT `tb_pelanggan_ibfk_1` FOREIGN KEY (`pel_id_user`) REFERENCES `tb_users` (`user_id`) ON UPDATE CASCADE,
  ADD CONSTRAINT `tb_pelanggan_ibfk_2` FOREIGN KEY (`pel_id_gol`) REFERENCES `tb_golongan` (`gol_id`) ON UPDATE CASCADE;
COMMIT;

/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
