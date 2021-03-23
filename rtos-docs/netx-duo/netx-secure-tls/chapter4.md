---
title: Rozdział 4 — Opis usług Azure RTO NetX Secure Services
description: Ten rozdział zawiera opis wszystkich NetX Secure Services (wymienionych poniżej) w porządku alfabetycznym.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89761ec3438b1b16c1a603764bf7d4e1eac1b4ea
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822854"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a><span data-ttu-id="d8319-103">Rozdział 4 — Opis usług Azure RTO NetX Secure Services</span><span class="sxs-lookup"><span data-stu-id="d8319-103">Chapter 4 - Description of Azure RTOS NetX Secure services</span></span>

<span data-ttu-id="d8319-104">Ten rozdział zawiera opis wszystkich usług Azure RTO NetX Secure Services (wymienionych poniżej) w porządku alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="d8319-104">This chapter contains a description of all Azure RTOS NetX Secure services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="d8319-105">W sekcji "wartości zwracane" w poniższych opisach interfejsu API wartości **pogrubione** nie mają wpływ na to, **NX_SECURE_DISABLE_ERROR_CHECKING** makro, które jest używane do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="d8319-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_SECURE_DISABLE_ERROR_CHECKING** macro that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="d8319-106">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="d8319-106">nx_secure_crypto_table_self_test</span></span>](#nx_secure_crypto_table_self_test)
  - <span data-ttu-id="d8319-107">Wykonaj self_test metod kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="d8319-107">Perform self_test on the crypto methods</span></span>
- [<span data-ttu-id="d8319-108">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="d8319-108">nx_secure_module_hash_compute</span></span>](#nx_secure_module_hash_compute)
  - <span data-ttu-id="d8319-109">Oblicza wartość skrótu przy użyciu funkcji skrótu user_supplied</span><span class="sxs-lookup"><span data-stu-id="d8319-109">Computes hash value using user_supplied hash function</span></span>
- [<span data-ttu-id="d8319-110">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="d8319-110">nx_secure_tls_active_certificate_set</span></span>](#nx_secure_tls_active_certificate_set)
  - <span data-ttu-id="d8319-111">Ustaw aktywny certyfikat tożsamości dla sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-111">Set the active identity certificate for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-112">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="d8319-112">nx_secure_tls_client_psk_set</span></span>](#nx_secure_tls_client_psk_set)
  - <span data-ttu-id="d8319-113">Ustaw klucz Pre_Shared dla sesji klienta Secure TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-113">Set a Pre_Shared Key for a NetX Secure TLS Client Session</span></span>
- [<span data-ttu-id="d8319-114">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-114">nx_secure_tls_initialize</span></span>](#nx_secure_tls_initialize)
  - <span data-ttu-id="d8319-115">Inicjuje moduł bezpiecznego protokołu TLS NetX]</span><span class="sxs-lookup"><span data-stu-id="d8319-115">Initializes the NetX Secure TLS module]</span></span>
- [<span data-ttu-id="d8319-116">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-116">nx_secure_tls_local_certificate_add</span></span>](#nx_secure_tls_local_certificate_add)
  - <span data-ttu-id="d8319-117">Dodawanie certyfikatu lokalnego do NetX bezpiecznej sesji protokołu TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-117">Add a local certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-118">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="d8319-118">nx_secure_tls_local_certificate_find</span></span>](#nx_secure_tls_local_certificate_find)
  - <span data-ttu-id="d8319-119">Znajdowanie certyfikatu lokalnego w NetX bezpiecznej sesji TLS według nazwy pospolitej</span><span class="sxs-lookup"><span data-stu-id="d8319-119">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>
- [<span data-ttu-id="d8319-120">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="d8319-120">nx_secure_tls_local_certificate_remove</span></span>](#nx_secure_tls_local_certificate_remove)
  - <span data-ttu-id="d8319-121">Usuń certyfikat lokalny z bezpiecznej sesji protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-121">Remove local certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-122">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="d8319-122">nx_secure_tls_metadata_size_calculate</span></span>](#nx_secure_tls_metadata_size_calculate)
  - <span data-ttu-id="d8319-123">Obliczanie rozmiaru metadanych kryptograficznych dla sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-123">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-124">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-124">nx_secure_tls_packet_allocate</span></span>](#nx_secure_tls_packet_allocate)
  - <span data-ttu-id="d8319-125">Przydziel pakiet dla sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-125">Allocate a packet for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-126">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="d8319-126">nx_secure_tls_psk_add</span></span>](#nx_secure_tls_psk_add)
  - <span data-ttu-id="d8319-127">Dodaj klucz Pre_Shared do sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-127">Add a Pre_Shared Key to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-128">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-128">nx_secure_tls_remote_certificate_allocate</span></span>](#nx_secure_tls_remote_certificate_allocate)
  - <span data-ttu-id="d8319-129">Przydzielanie miejsca dla certyfikatu dostarczonego przez hosta zdalnego protokołu TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-129">Allocate space for the certificate provided by a remote TLS host</span></span>
- [<span data-ttu-id="d8319-130">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-130">nx_secure_tls_remote_certificate_buffer_allocate</span></span>](#nx_secure_tls_remote_certificate_buffer_allocate)
  - <span data-ttu-id="d8319-131">Przydzielanie miejsca dla wszystkich certyfikatów dostarczonych przez zdalnego hosta protokołu TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-131">Allocate space for all certificates provided by a remote TLS host</span></span>
- [<span data-ttu-id="d8319-132">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="d8319-132">nx_secure_tls_remote_certificate_free_all</span></span>](#nx_secure_tls_remote_certificate_free_all)
  - <span data-ttu-id="d8319-133">Wolne miejsce przydzielono dla certyfikatów przychodzących</span><span class="sxs-lookup"><span data-stu-id="d8319-133">Free space allocated for incoming certificates</span></span>
- [<span data-ttu-id="d8319-134">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-134">nx_secure_tls_server_certificate_add</span></span>](#nx_secure_tls_server_certificate_add)
  - <span data-ttu-id="d8319-135">Dodawanie certyfikatu przeznaczonego dla serwerów TLS przy użyciu identyfikatora liczbowego</span><span class="sxs-lookup"><span data-stu-id="d8319-135">Add a certificate specifically for TLS servers using a numeric identifier</span></span>
- [<span data-ttu-id="d8319-136">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="d8319-136">nx_secure_tls_server_certificate_find</span></span>](#nx_secure_tls_server_certificate_find)
  - <span data-ttu-id="d8319-137">Znajdowanie certyfikatu przy użyciu identyfikatora liczbowego</span><span class="sxs-lookup"><span data-stu-id="d8319-137">Find a certificate using a numeric identifier</span></span>
- [<span data-ttu-id="d8319-138">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="d8319-138">nx_secure_tls_server_certificate_remove</span></span>](#nx_secure_tls_server_certificate_remove)
  - <span data-ttu-id="d8319-139">Usuwanie certyfikatu serwera lokalnego przy użyciu identyfikatora liczbowego</span><span class="sxs-lookup"><span data-stu-id="d8319-139">Remove a local server certificate using a numeric identifier</span></span>
- [<span data-ttu-id="d8319-140">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-140">nx_secure_tls_session_certificate_callback_set</span></span>](#nx_secure_tls_session_certificate_callback_set)
  - <span data-ttu-id="d8319-141">Konfigurowanie wywołania zwrotnego protokołu TLS do użycia na potrzeby dodatkowej weryfikacji certyfikatu</span><span class="sxs-lookup"><span data-stu-id="d8319-141">Set up a callback for TLS to use for additional certificate validation</span></span>
- [<span data-ttu-id="d8319-142">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-142">nx_secure_tls_session_client_callback_set</span></span>](#nx_secure_tls_session_client_callback_set)
  - <span data-ttu-id="d8319-143">Konfigurowanie wywołania zwrotnego protokołu TLS do wywołania na początku uzgadniania klienta TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-143">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>
- [<span data-ttu-id="d8319-144">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="d8319-144">nx_secure_tls_session_x509_client_verify_configure</span></span>](#nx_secure_tls_session_x509_client_verify_configure)
  - <span data-ttu-id="d8319-145">Włącz weryfikację klienta X. 509 i Przydziel miejsce dla certyfikatów klienta</span><span class="sxs-lookup"><span data-stu-id="d8319-145">Enable client X.509 verification and allocate space for client certificates</span></span>
- [<span data-ttu-id="d8319-146">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="d8319-146">nx_secure_tls_session_client_verify_disable</span></span>](#nx_secure_tls_session_client_verify_disable)
  - <span data-ttu-id="d8319-147">Wyłączanie uwierzytelniania certyfikatu klienta dla sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-147">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-148">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="d8319-148">nx_secure_tls_session_client_verify_enable</span></span>](#nx_secure_tls_session_client_verify_enable)
  - <span data-ttu-id="d8319-149">Włącz uwierzytelnianie certyfikatu klienta dla sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-149">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-150">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-150">nx_secure_tls_session_create</span></span>](#nx_secure_tls_session_create)
  - <span data-ttu-id="d8319-151">Tworzenie bezpiecznej sesji protokołu TLS NetX na potrzeby bezpiecznej komunikacji</span><span class="sxs-lookup"><span data-stu-id="d8319-151">Create a NetX Secure TLS Session for secure communications</span></span>
- [<span data-ttu-id="d8319-152">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="d8319-152">nx_secure_tls_session_delete</span></span>](#nx_secure_tls_session_delete)
  - <span data-ttu-id="d8319-153">Usuwanie sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-153">Delete a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-154">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="d8319-154">nx_secure_tls_session_end</span></span>](#nx_secure_tls_session_end)
  - <span data-ttu-id="d8319-155">Kończenie aktywnej sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-155">End an active NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-156">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="d8319-156">nx_secure_tls_session_packet_buffer_set</span></span>](#nx_secure_tls_session_packet_buffer_set)
  - <span data-ttu-id="d8319-157">Ustawianie buforu ponownego zestawu pakietów dla sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-157">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-158">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="d8319-158">nx_secure_tls_session_protocol_version_override</span></span>](#nx_secure_tls_session_protocol_version_override)
  - <span data-ttu-id="d8319-159">Zastąp domyślną wersję protokołu TLS dla sesji Secure TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-159">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-160">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-160">nx_secure_tls_session_receive</span></span>](#nx_secure_tls_session_receive)
  - <span data-ttu-id="d8319-161">Odbieranie danych z bezpiecznej sesji protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-161">Receive data from a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-162">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-162">nx_secure_tls_session_renegotiate_callback_set</span></span>](#nx_secure_tls_session_renegotiate_callback_set)
  - <span data-ttu-id="d8319-163">Przypisanie wywołania zwrotnego, które zostanie wywołane na początku ponownej negocjacji sesji</span><span class="sxs-lookup"><span data-stu-id="d8319-163">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>
- [<span data-ttu-id="d8319-164">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="d8319-164">nx_secure_tls_session_renegotiate</span></span>](#nx_secure_tls_session_renegotiate)
  - <span data-ttu-id="d8319-165">Inicjowanie uzgadniania sesji z hostem zdalnym</span><span class="sxs-lookup"><span data-stu-id="d8319-165">Initiate a session renegotiation handshake with the remote host</span></span>
- [<span data-ttu-id="d8319-166">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="d8319-166">nx_secure_tls_session_reset</span></span>](#nx_secure_tls_session_reset)
  - <span data-ttu-id="d8319-167">Wyczyść i zresetuj bezpieczną sesję protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-167">Clear out and reset a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-168">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="d8319-168">nx_secure_tls_session_send</span></span>](#nx_secure_tls_session_send)
  - <span data-ttu-id="d8319-169">Wysyłanie danych za pomocą zabezpieczonej sesji protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-169">Send data through a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-170">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-170">nx_secure_tls_session_server_callback_set</span></span>](#nx_secure_tls_session_server_callback_set)
  - <span data-ttu-id="d8319-171">Skonfiguruj wywołanie zwrotne protokołu TLS do wywołania na początku uzgadniania serwera TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-171">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>
- [<span data-ttu-id="d8319-172">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="d8319-172">nx_secure_tls_session_sni_extension_parse</span></span>](#nx_secure_tls_session_sni_extension_parse)
  - <span data-ttu-id="d8319-173">Analizowanie rozszerzenia Oznaczanie nazwy serwera (SNI) otrzymanego z klienta TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-173">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>
- [<span data-ttu-id="d8319-174">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="d8319-174">nx_secure_tls_session_sni_extension_set</span></span>](#nx_secure_tls_session_sni_extension_set)
  - <span data-ttu-id="d8319-175">Ustaw nazwę DNS rozszerzenia Oznaczanie nazwy serwera (SNI) na wysyłanie do serwera zdalnego</span><span class="sxs-lookup"><span data-stu-id="d8319-175">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>
- [<span data-ttu-id="d8319-176">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-176">nx_secure_tls_session_start</span></span>](#nx_secure_tls_session_start)
  - <span data-ttu-id="d8319-177">Rozpocznij sesję bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-177">Start a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-178">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="d8319-178">nx_secure_tls_session_time_function_set</span></span>](#nx_secure_tls_session_time_function_set)
  - <span data-ttu-id="d8319-179">Przypisywanie funkcji sygnatury czasowej do NetX bezpiecznej sesji TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-179">Assign a timestamp function to a NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-180">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-180">nx_secure_tls_trusted_certificate_add</span></span>](#nx_secure_tls_trusted_certificate_add)
  - <span data-ttu-id="d8319-181">Dodaj zaufany certyfikat do NetX bezpiecznej sesji TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-181">Add trusted certificate to NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-182">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="d8319-182">nx_secure_tls_trusted_certificate_remove</span></span>](#nx_secure_tls_trusted_certificate_remove)
  - <span data-ttu-id="d8319-183">Usuń zaufany certyfikat z bezpiecznej sesji protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-183">Remove trusted certificate from NetX Secure TLS Session</span></span>
- [<span data-ttu-id="d8319-184">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-184">nx_secure_x509_certificate_initialize</span></span>](#nx_secure_x509_certificate_initialize)
  - <span data-ttu-id="d8319-185">Zainicjuj certyfikat X. 509 dla usługi NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-185">Initialize X.509 Certificate for NetX Secure TLS</span></span>
- [<span data-ttu-id="d8319-186">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="d8319-186">nx_secure_x509_common_name_dns_check</span></span>](#nx_secure_x509_common_name_dns_check)
  - <span data-ttu-id="d8319-187">Sprawdź nazwę DNS w odniesieniu do certyfikatu X. 509</span><span class="sxs-lookup"><span data-stu-id="d8319-187">Check DNS name against X.509 Certificate</span></span>
- [<span data-ttu-id="d8319-188">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="d8319-188">nx_secure_x509_crl_revocation_check</span></span>](#nx_secure_x509_crl_revocation_check)
  - <span data-ttu-id="d8319-189">Sprawdź certyfikat X. 509 względem podanej listy odwołania certyfikatów (CRL)]</span><span class="sxs-lookup"><span data-stu-id="d8319-189">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)]</span></span>
- [<span data-ttu-id="d8319-190">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-190">nx_secure_x509_dns_name_initialize</span></span>](#nx_secure_x509_dns_name_initialize)
  - <span data-ttu-id="d8319-191">Zainicjuj strukturę nazw DNS X. 509</span><span class="sxs-lookup"><span data-stu-id="d8319-191">Initialize an X.509 DNS name structure</span></span>
- [<span data-ttu-id="d8319-192">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="d8319-192">nx_secure_x509_extended_key_usage_extension_parse</span></span>](#nx_secure_x509_extended_key_usage_extension_parse)
  - <span data-ttu-id="d8319-193">Znajdowanie i analizowanie rozszerzenia rozszerzonego użycia klucza X. 509 w certyfikacie X. 509</span><span class="sxs-lookup"><span data-stu-id="d8319-193">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>
- [<span data-ttu-id="d8319-194">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="d8319-194">nx_secure_x509_extension_find</span></span>](#nx_secure_x509_extension_find)
  - <span data-ttu-id="d8319-195">Znajdź i zwróć rozszerzenie X. 509 w certyfikacie X. 509</span><span class="sxs-lookup"><span data-stu-id="d8319-195">Find and return an X.509 extension in an X.509 certificate</span></span>
- [<span data-ttu-id="d8319-196">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="d8319-196">nx_secure_x509_key_usage_extension_parse</span></span>](#nx_secure_x509_key_usage_extension_parse)
  - <span data-ttu-id="d8319-197">Znajdź i Przeanalizuj rozszerzenie użycie klucza X. 509 w certyfikacie X. 509</span><span class="sxs-lookup"><span data-stu-id="d8319-197">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

## <a name="nx_secure_crypto_table_self_test"></a><span data-ttu-id="d8319-198">nx_secure_crypto_table_self_test</span><span class="sxs-lookup"><span data-stu-id="d8319-198">nx_secure_crypto_table_self_test</span></span>

<span data-ttu-id="d8319-199">Wykonaj własne Testowanie metod kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="d8319-199">Perform self-test on the crypto methods</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-200">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-200">Prototype</span></span>

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a><span data-ttu-id="d8319-201">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-201">Description</span></span>

<span data-ttu-id="d8319-202">Ta usługa jest uruchamiana za pomocą testów metod kryptograficznych, aby sprawdzić poprawność.</span><span class="sxs-lookup"><span data-stu-id="d8319-202">This service runs through the crypto method self tests to validate.</span></span> <span data-ttu-id="d8319-203">Test samodzielny jest dostępny tylko wtedy, gdy biblioteka NetX Secure została skompilowana z symbolem zdefiniowanym NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK.</span><span class="sxs-lookup"><span data-stu-id="d8319-203">The self test is available only if NetX Secure library is built with the symbol NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK defined.</span></span>

<span data-ttu-id="d8319-204">Dla każdej obsługiwanej metody kryptograficznej, autotest dostarcza wstępnie zdefiniowane dane wejściowe i zweryfikowane dane wyjściowe są zgodne ze wstępnie zdefiniowaną wartością oczekiwaną.</span><span class="sxs-lookup"><span data-stu-id="d8319-204">For each supported crypto method, the self test provides pre-defined input data, and verified the output matches the pre-defined expected value.</span></span>

<span data-ttu-id="d8319-205">Bezpieczny samotest kryptograficzny NetX obsługuje następujące algorytmy i rozmiary kluczy:</span><span class="sxs-lookup"><span data-stu-id="d8319-205">NetX Secure crypto self test supports the following algorithms and key sizes:</span></span>

- <span data-ttu-id="d8319-206">DES: szyfrowanie i odszyfrowywanie</span><span class="sxs-lookup"><span data-stu-id="d8319-206">DES: encryption and decryption</span></span>
- <span data-ttu-id="d8319-207">Triple DES (3DES): szyfrowanie i odszyfrowywanie</span><span class="sxs-lookup"><span data-stu-id="d8319-207">Triple DES (3DES): encryption and decryption</span></span>
- <span data-ttu-id="d8319-208">AES: 128-, 192-, 256-bitowy rozmiar klucza, szyfrowanie i odszyfrowywanie, w trybie CBC i w trybie licznika.</span><span class="sxs-lookup"><span data-stu-id="d8319-208">AES: 128-, 192-, 256-bit key size, encryption and decryption, in CBC mode and counter mode.</span></span>
- <span data-ttu-id="d8319-209">HMAC-MD5: uwierzytelnianie i obliczanie wartości skrótu</span><span class="sxs-lookup"><span data-stu-id="d8319-209">HMAC-MD5: authentication and hash computation</span></span>
- <span data-ttu-id="d8319-210">HMAC-SHA: SHA1-96, SHA1-160, algorytmu SHA2-256, algorytmu SHA2-384, algorytmu SHA2-512, uwierzytelnianie i obliczanie wartości skrótu</span><span class="sxs-lookup"><span data-stu-id="d8319-210">HMAC-SHA: SHA1-96, SHA1-160, SHA2-256, SHA2-384, SHA2- 512, authentication and hash computation</span></span>
- <span data-ttu-id="d8319-211">MD5: uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="d8319-211">MD5: authentication</span></span>
- <span data-ttu-id="d8319-212">Funkcja pseudo-Losowa (PRF): PRF_HMAC_SHA1 i PRF_HMAC_SHA2-256</span><span class="sxs-lookup"><span data-stu-id="d8319-212">Pseudo-random Function (PRF): PRF_HMAC_SHA1 and PRF_HMAC_SHA2-256</span></span>
- <span data-ttu-id="d8319-213">RSA: 1024-, 2048-, 4096-bit-bitowego operacji dla modułu RSA</span><span class="sxs-lookup"><span data-stu-id="d8319-213">RSA: 1024-, 2048-, 4096-bit RSA power-modulus operation</span></span>
- <span data-ttu-id="d8319-214">SHA: SHA1 (96-i 160-bitowe), algorytmu SHA2 (256bit, 384bit, 512bit)</span><span class="sxs-lookup"><span data-stu-id="d8319-214">SHA: SHA1 (96- and 160-bit), SHA2 (256bit, 384bit, 512bit) authentication</span></span>

<span data-ttu-id="d8319-215">Ta funkcja ma wbudowane wektory dla algorytmów kryptograficznych wymienionych powyżej.</span><span class="sxs-lookup"><span data-stu-id="d8319-215">This function has the built-in vectors for the crypto algorithms listed above.</span></span> <span data-ttu-id="d8319-216">Jednak testuje tylko te wymienione w *cipher_table* przekazaną do tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d8319-216">However it only tests the ones listed in the *cipher_table* passed into this function.</span></span> <span data-ttu-id="d8319-217">Na przykład w przypadku sesji TLS używa tylko TLS_RSA_WITH_AES_128_CBC_SHA ciphersuite, ta funkcja przeprowadzi autotest na RSA (1024-, 2048-, 4096-bit), AES-CBC (128-bit) i SHA1.</span><span class="sxs-lookup"><span data-stu-id="d8319-217">For example, for a TLS session uses only the ciphersuite TLS_RSA_WITH_AES_128_CBC_SHA, this function will perform self test on the RSA (1024-, 2048-, 4096-bit), AES-CBC (128-bit) and SHA1.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-218">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-218">Parameters</span></span>

- <span data-ttu-id="d8319-219">**crypto_table** Wskaźnik do tabeli kryptograficznej używanej przez sesję TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-219">**crypto_table** Pointer to the crypto table being used by the TLS session.</span></span> <span data-ttu-id="d8319-220">Jest to ten sam crypto_table, który jest przesyłany do wywołania **_nx_secure_tls_session_create ()_** .</span><span class="sxs-lookup"><span data-stu-id="d8319-220">This is the same crypto_table being passed into the **_nx_secure_tls_session_create()_** call.</span></span>
- <span data-ttu-id="d8319-221">**metadane** Wskaźnik na miejsce dla obszaru metadanych kryptografii.</span><span class="sxs-lookup"><span data-stu-id="d8319-221">**metadata** Pointer to space for cryptography metadata area.</span></span> <span data-ttu-id="d8319-222">.</span><span class="sxs-lookup"><span data-stu-id="d8319-222">.</span></span>
- <span data-ttu-id="d8319-223">**metadata_size** Rozmiar buforu metadanych.</span><span class="sxs-lookup"><span data-stu-id="d8319-223">**metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-224">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-224">Return Values</span></span>

- <span data-ttu-id="d8319-225">**NX_SECURE_TLS_SUCCESS** (0X00) pomyślnie przetestowała dostarczone metody kryptograficzne.</span><span class="sxs-lookup"><span data-stu-id="d8319-225">**NX_SECURE_TLS_SUCCESS** (0x00) Successfully tested the crypto methods provided.</span></span>
- <span data-ttu-id="d8319-226">**NX_PTR_ERROR** (0X07) Nieprawidłowa struktura metody kryptograficznej</span><span class="sxs-lookup"><span data-stu-id="d8319-226">**NX_PTR_ERROR** (0x07) Invalid crypto method structure</span></span>
- <span data-ttu-id="d8319-227">**NX_NOT_SUCCESSFUL** (0x43) samotest kryptograficzny nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="d8319-227">**NX_NOT_SUCCESSFUL** (0x43) Crypto self test fails.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-228">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-228">Allowed From</span></span>

<span data-ttu-id="d8319-229">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-229">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-230">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-230">Example</span></span>

```C
/* crypto_tls_ciphers is the cipher table for the TLS session. */
/* metadata_buffer is the memory area used by the cipher functions. */

/* The following function verifies the supplied ciphersuties using the built-in
   self test. */

if (nx_secure_crypto_table_self_test(&crypto_tls_ciphers, metadata_buffer,
    sizeof(metadata_buffer)))
{
    printf("Crypto self test failed!\r\n");
    exit(0);
}
else
{
    printf("Crypto self test succeed!\r\n");
}

/* Now the ciphersuites are successfully test, it can be used in
   nx_secure_tls_session_create() */
```

### <a name="see-also"></a><span data-ttu-id="d8319-231">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-231">See Also</span></span>

- <span data-ttu-id="d8319-232">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-232">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_module_hash_compute"></a><span data-ttu-id="d8319-233">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="d8319-233">nx_secure_module_hash_compute</span></span>

<span data-ttu-id="d8319-234">Oblicza wartość skrótu przy użyciu funkcji skrótu dostarczonej przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="d8319-234">Computes hash value using user-supplied hash function</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-235">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-235">Prototype</span></span>

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="d8319-236">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-236">Description</span></span>

<span data-ttu-id="d8319-237">Ta funkcja oblicza wartość skrótu strumienia danych w określonym obszarze pamięci przy użyciu dostarczonej metody kryptograficznej HMAC i ciągu klucza.</span><span class="sxs-lookup"><span data-stu-id="d8319-237">This function computes the hash value of the data stream in the specified memory area, using supplied HMAC crypto method and the key string.</span></span> <span data-ttu-id="d8319-238">Funkcja obliczania skrótu modułu jest dostępna tylko wtedy, gdy biblioteka NetX Secure została skompilowana przy użyciu następującego zdefiniowanego symbolu: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span><span class="sxs-lookup"><span data-stu-id="d8319-238">The module hash compute function is available only if NetX Secure library is built with the following symbol being defined: NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-239">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-239">Parameters</span></span>

- <span data-ttu-id="d8319-240">**hmac_ptr** Wskaźnik do metody kryptograficznej HMAC używanej do obliczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="d8319-240">**hmac_ptr** Pointer to the HMAC crypto method being used for the hash value computation.</span></span>
- <span data-ttu-id="d8319-241">**start_address** Adres początkowy buforu danych</span><span class="sxs-lookup"><span data-stu-id="d8319-241">**start_address** The starting address of the data buffer</span></span>
- <span data-ttu-id="d8319-242">**end_address** Adres końcowy buforu danych.</span><span class="sxs-lookup"><span data-stu-id="d8319-242">**end_address** The ending address of the data buffer.</span></span> <span data-ttu-id="d8319-243">Należy zauważyć, że obliczenia skrótu nie obejmują danych w tym end_address.</span><span class="sxs-lookup"><span data-stu-id="d8319-243">Note that hash computation does not cover the data at this end_address.</span></span>
- <span data-ttu-id="d8319-244">**klucz** Ciąg klucza używany w obliczeniach HMAC.</span><span class="sxs-lookup"><span data-stu-id="d8319-244">**key** The key string being used in the HMAC computation.</span></span>
- <span data-ttu-id="d8319-245">**key_length** Rozmiar ciągu klucza w bajtach</span><span class="sxs-lookup"><span data-stu-id="d8319-245">**key_length** The size of the key string, in bytes</span></span>
- <span data-ttu-id="d8319-246">**metadane** Wskaźnik do miejsca używanego przez Algorytm HMAC.</span><span class="sxs-lookup"><span data-stu-id="d8319-246">**metadata** Pointer to space used by the HMAC algorithm.</span></span>
- <span data-ttu-id="d8319-247">**metadata_size** Rozmiar buforu metadanych.</span><span class="sxs-lookup"><span data-stu-id="d8319-247">**metadata_size** Size of the metadata buffer.</span></span>
- <span data-ttu-id="d8319-248">**output_buffer** Lokalizacja pamięci, w której jest przechowywane dane wyjściowe skrótu.</span><span class="sxs-lookup"><span data-stu-id="d8319-248">**output_buffer** The memory location where the hash output is being stored at.</span></span>
- <span data-ttu-id="d8319-249">**output_buffer_size** Dostępne miejsce w buforze wyjściowym (w bajtach)</span><span class="sxs-lookup"><span data-stu-id="d8319-249">**output_buffer_size** The available space of the output buffer, in bytes</span></span>
- <span data-ttu-id="d8319-250">**actual_size** Zwrócone przez funkcję wskazującą rzeczywistą liczbę bajtów zapisywanych w output_buffer.</span><span class="sxs-lookup"><span data-stu-id="d8319-250">**actual_size** Returned by the function indicating the actual number of bytes being written into the output_buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-251">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-251">Return Values</span></span>

- <span data-ttu-id="d8319-252">**0** pomyślnie przeliczył wartość skrótu.</span><span class="sxs-lookup"><span data-stu-id="d8319-252">**0** Successfully computed the hash value.</span></span>
- <span data-ttu-id="d8319-253">**1** Obliczanie skrótu nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="d8319-253">**1** The hash computation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-254">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-254">Allowed From</span></span>

<span data-ttu-id="d8319-255">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-255">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-256">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-256">Example</span></span>

```C
/* Define the HMAC SHA256 method */
NX_CRYPTO_METHOD hmac_sha256 =
{
    NX_CRYPTO_AUTHENTICATION_HMAC_SHA2_256,    /* HMAC SHA256 algorithm  */
    0,                                         /* Key size, not used     */
    0,                                         /* IV size, not used      */
    NX_CRYPTO_HMAC_SHA256_ICV_FULL_LEN_IN_BITS,/* Transmitted ICV size   */
    NX_CRYPTO_SHA2_BLOCK_SIZE_IN_BYTES,        /* Block size in bytes    */
    sizeof(NX_CRYPTO_SHA256_HMAC),             /* Metadata size in bytes */
    _nx_crypto_method_hmac_sha256_init,        /* HMAC SHA256 init       */
    _nx_crypto_method_hmac_sha256_cleanup,     /* HMAC SHA256 cleanup    */
    _nx_crypto_method_hmac_sha256_operation    /* HMAC SHA256 operation  */
};

/* Define the hash key being used. */
const CHAR hash_key = “my hash key”;

/* Define starting address. */
UINT starting_address = 0x10000;

/* Define the ending address.
   Note that the hash computation covers the memory location
   before the ending address. */
UINT ending_address = 0x11000;

/* Declare the output buffer. */
#define OUTPUT_BUFFER_SIZE
UCHAR output_buffer[OUTPUT_BUFFER_SIZE];

UINT actual_size;

/* Declare 1K bytes of metadata buffer area. */
UCHAR metadata_buffer[1024];

/* Compute the hash value of the data between 0x10000 – 0x10FFF */
nx_secure_module_hash_compute(&hmac_sha256,
                              starting_address, ending_address,
                              hash_key, strlen(hash_key),
                              metadata_buffer, sizeof(metadata_buffer),
                              output_buffer, OUTPUT_BUFFER_SIZE, &actual_size);

/* If this function returns “0”, the hash value has been computed and is stored
   in output_buffer. */
```

### <a name="see-also"></a><span data-ttu-id="d8319-257">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-257">See Also</span></span>

- <span data-ttu-id="d8319-258">nx_secure_crypto_method_self_test</span><span class="sxs-lookup"><span data-stu-id="d8319-258">nx_secure_crypto_method_self_test</span></span>

## <a name="nx_secure_tls_active_certificate_set"></a><span data-ttu-id="d8319-259">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="d8319-259">nx_secure_tls_active_certificate_set</span></span>

<span data-ttu-id="d8319-260">Ustaw aktywny certyfikat tożsamości dla sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-260">Set the active identity certificate for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-261">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-261">Prototype</span></span>

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="d8319-262">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-262">Description</span></span>

<span data-ttu-id="d8319-263">Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego sesji (zobacz nx_secure_tls_session_client_callback_set i nx_secure_tls_session_server_callback_set).</span><span class="sxs-lookup"><span data-stu-id="d8319-263">This service is intended to be called from within a session callback (see nx_secure_tls_session_client_callback_set and nx_secure_tls_session_server_callback_set).</span></span> <span data-ttu-id="d8319-264">Gdy jest wywoływana z wcześniej zainicjowaną strukturą NX_SECURE_X509_CERT, ten certyfikat będzie używany zamiast domyślnego certyfikatu tożsamości.</span><span class="sxs-lookup"><span data-stu-id="d8319-264">When called with a previously-initialized NX_SECURE_X509_CERT structure, that certificate will be used instead of the default identity certificate.</span></span> <span data-ttu-id="d8319-265">W większości przypadków certyfikat należy dodać do magazynu lokalnego (zobacz nx_secure_tls_local_certificate_add) lub uzgadnianie protokołu TLS może zakończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d8319-265">In most cases, the certificate must have been added to the local store (see nx_secure_tls_local_certificate_add) or the TLS handshake may fail.</span></span>

<span data-ttu-id="d8319-266">Ta usługa ma pozwolić, aby protokół TLS obsługiwał wiele certyfikatów tożsamości.</span><span class="sxs-lookup"><span data-stu-id="d8319-266">This service is intended to allow TLS to support multiple identity certificates.</span></span> <span data-ttu-id="d8319-267">Jest to przydatne w przypadku serwera TLS z wieloma adresami sieciowymi, dzięki czemu serwer może wybrać odpowiedni certyfikat do udostępnienia klientowi zdalnemu w zależności od punktu wejścia klienta.</span><span class="sxs-lookup"><span data-stu-id="d8319-267">This is useful for a TLS server that services multiple network addresses so the server can pick an appropriate certificate to provide to the remote client depending on the client's entrypoint.</span></span> <span data-ttu-id="d8319-268">W przypadku klienta TLS ta procedura może służyć do zmiany certyfikatu wysłanego do zdalnego serwera w czasie wykonywania po zidentyfikowaniu serwera w uzgadnianiu TLS (jest to trudniejsze niż w przypadku użycia serwera TLS).</span><span class="sxs-lookup"><span data-stu-id="d8319-268">For a TLS client, this routine may be used to change the certificate sent to a remote server at runtime after the server has identified itself in the TLS handshake (this is more rare than the TLS server use-case).</span></span>

<span data-ttu-id="d8319-269">W przypadku, gdy wiele certyfikatów może współużytkować tę samą nazwę wyróżniającą X. 509, należy dodać certyfikaty przy użyciu nx_secure_tls_server_certificate_add, co wprowadza identyfikator liczbowy oddzielny od certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-269">In the case where multiple certificates may share the same X.509 distinguished name, certificates will need to be added using nx_secure_tls_server_certificate_add, which introduces a numeric identifier separate from the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-270">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-270">Parameters</span></span>

- <span data-ttu-id="d8319-271">**session_ptr** Wskaźnik do wystąpienia sesji TLS przeszedł do wywołania zwrotnego sesji.</span><span class="sxs-lookup"><span data-stu-id="d8319-271">**session_ptr** Pointer to a TLS Session instance passed into the session callback.</span></span>
- <span data-ttu-id="d8319-272">**certyfikat** Wskaźnik na zainicjowany certyfikat X. 509, który ma być używany dla bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="d8319-272">**certificate** Pointer to an initialized X.509 certificate that is to be used for the current session.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-273">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-273">Return Values</span></span>

- <span data-ttu-id="d8319-274">**NX_SUCCESS** (0x00) — pomyślne przypisanie certyfikatu do sesji.</span><span class="sxs-lookup"><span data-stu-id="d8319-274">**NX_SUCCESS** (0x00) Successful assignment of certificate to session.</span></span>
- <span data-ttu-id="d8319-275">**NX_PTR_ERROR** (0X07) Nieprawidłowa sesja protokołu TLS lub wskaźnik certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-275">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-276">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-276">Allowed From</span></span>

<span data-ttu-id="d8319-277">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-278">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-278">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”
#define TLS_DEFAULT_SERVER_CERT_ID 2
#define TLS_EXAMPLE_CERT_ID 3


/* Callback for ClientHello extensions processing. */
static ULONG tls_server_callback(NX_SECURE_TLS_SESSION *tls_session,
                                 NX_SECURE_TLS_HELLO_EXTENSION *extensions,
                                 UINT num_extensions)
{
NX_SECURE_X509_DNS_NAME dns_name;
INT compare_value;
UINT status;
NX_SECURE_X509_CERT *cert_ptr;

    /* Grab a pointer to our default certificate in case the SNI extension is not
       available or the specified server name is unknown. */
    nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                     TLS_DEFAULT_SERVER_CERT_ID);


    /* Process Server Name Indication extension. */
    status = _nx_secure_tls_session_sni_extension_parse(tls_session, extensions,
                                                    num_extensions, &dns_name);

    /* If no extension found, that is OK. Use default certificate. */
    if(status == NX_SUCCESS)
    {
          /* SNI extension found, select an active certificate based on the server
             name. */

          /* Make sure our SNI name matches. */
          compare_value = memcmp(dns_name.nx_secure_x509_dns_name,
                                TLS_SNI_SERVER_NAME, strlen(TLS_SNI_SERVER_NAME));

          if(compare_value == 0 && dns_name.nx_secure_x509_dns_name_length !=
             strlen(TLS_SNI_SERVER_NAME))
          {
             /* Found a match, find the certificate we want to use. */
             _nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                                      TLS_EXAMPLE_CERT_ID);
          }
          else
          {
             /* No matching server name found. The application may choose to simply
                provide the default certificate (and probably resulting in an error
                in the remote client) or returning an error here to end the
                handshake. A user-defined non-zero error code will be sufficient –
                the error code will abort the TLS handshake and be returned to the
                caller that started the server. */
                return(0x500);
          }
      }
      else
      {
      }
      /* Set the certificate we want to use. */
      nx_secure_tls_active_certificate_set(tls_session, cert_ptr);

      /* Return success to continue TLS handshake. */
      return(NX_SUCCESS);
}

/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_TLS_SESSION server_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&server_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_tls_session_create: 0x%x\n", status);
    }

    /* Setup our packet reassembly buffer. See
       nx_secure_tls_session_packet_buffer_set for more information. */
    nx_secure_tls_session_packet_buffer_set(&server_tls_session,
                                      server_packet_buffer,
                                      sizeof(server_packet_buffer));


    /* Set callback for server TLS extension handling. */
    _nx_secure_tls_session_server_callback_set(&server_tls_session,
                                              tls_server_callback);

    /* Initialize our certificates – certificate data defined elsewhere. See
       section “Importing X.509 Certificates into NetX Secure” for more
       information. */
    nx_secure_x509_certificate_initialize(&default_certificate,
                                      default_cert_der,
                                      default _cert_der_len, NX_NULL, 0,
                                      default_cert_key_der,
                                      default_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &default_certificate,
                                         TLS_DEFAULT_SERVER_CERT_ID);

    /* Alternative identity certificate, needs to have a private key! */
    nx_secure_x509_certificate_initialize(&example_certificate,
                                      example_cert_der,
                                      example cert_der_len, NX_NULL, 0,
                                      example_cert_key_der,
                                      example_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &example_certificate,
                                         TLS_EXAMPLE_CERT_ID);

    /* Now we can start the TLS session as normal. */
       …
}
```

### <a name="see-also"></a><span data-ttu-id="d8319-279">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-279">See Also</span></span>

- <span data-ttu-id="d8319-280">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-280">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-281">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-281">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="d8319-282">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-282">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="d8319-283">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-283">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="d8319-284">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-284">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="d8319-285">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="d8319-285">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="d8319-286">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="d8319-286">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_client_psk_set"></a><span data-ttu-id="d8319-287">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="d8319-287">nx_secure_tls_client_psk_set</span></span>

<span data-ttu-id="d8319-288">Ustaw klucz wstępny dla sesji klienta Secure TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-288">Set a Pre-Shared Key for a NetX Secure TLS Client Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-289">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-289">Prototype</span></span>

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a><span data-ttu-id="d8319-290">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-290">Description</span></span>

<span data-ttu-id="d8319-291">Ta usługa dodaje klucz wstępny (PSK), jego ciąg tożsamości i wskazówkę dotyczącą tożsamości do bloku kontroli sesji protokołu TLS i ustawia, że klucz PSK ma być używany w kolejnych połączeniach klientów TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-291">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block, and sets that PSK to be used in subsequent TLS Client connections.</span></span> <span data-ttu-id="d8319-292">PSK jest używany zamiast certyfikatu cyfrowego, gdy ciphersuites PSK są włączone i używane.</span><span class="sxs-lookup"><span data-stu-id="d8319-292">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

<span data-ttu-id="d8319-293">W takim przypadku PSK jest skojarzony z określonym zdalnym serwerem protokołu TLS, z którym klient protokołu TLS chce się komunikować.</span><span class="sxs-lookup"><span data-stu-id="d8319-293">In this case, the PSK is associated with a specific remote TLS Server with which the TLS Client wishes to communicate.</span></span> <span data-ttu-id="d8319-294">Zestaw PSK ustawiony za pomocą tego interfejsu API zostanie udostępniony hostowi zdalnego protokołu TLS podczas kolejnego uzgadniania protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-294">The PSK set through this API will be provided to the remote TLS Server host during the next TLS handshake.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-295">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-295">Parameters</span></span>

- <span data-ttu-id="d8319-296">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-296">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="d8319-297">**pre_shared_key** Rzeczywista wartość klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="d8319-297">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="d8319-298">**psk_length** Długość wartości klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="d8319-298">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="d8319-299">**psk_identity** Ciąg służący do identyfikowania tej wartości PSK.</span><span class="sxs-lookup"><span data-stu-id="d8319-299">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="d8319-300">**identity_length** Długość tożsamości PSK.</span><span class="sxs-lookup"><span data-stu-id="d8319-300">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="d8319-301">**Wskazówka** Ciąg używany do wskazania grupy PSKs do wyboru na serwerze TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-301">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="d8319-302">**hint_length** Długość ciągu wskazówki.</span><span class="sxs-lookup"><span data-stu-id="d8319-302">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-303">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-303">Return Values</span></span>

- <span data-ttu-id="d8319-304">**NX_SUCCESS** (0X00) pomyślne dodanie klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="d8319-304">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="d8319-305">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-305">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="d8319-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) nie może dodać innego klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="d8319-306">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-307">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-307">Allowed From</span></span>

<span data-ttu-id="d8319-308">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-308">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-309">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-309">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-310">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-310">See Also</span></span>

- <span data-ttu-id="d8319-311">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="d8319-311">nx_secure_tls_psk_add</span></span>
- <span data-ttu-id="d8319-312">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-312">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-313">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-313">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-314">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-314">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-315">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-315">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_initialize"></a><span data-ttu-id="d8319-316">nx_secure_tls_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-316">nx_secure_tls_initialize</span></span>

<span data-ttu-id="d8319-317">Inicjuje moduł bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-317">Initializes the NetX Secure TLS module</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-318">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-318">Prototype</span></span>

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="d8319-319">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-319">Description</span></span>

<span data-ttu-id="d8319-320">Ta usługa Inicjuje moduł bezpiecznego protokołu TLS NetX.</span><span class="sxs-lookup"><span data-stu-id="d8319-320">This service initializes the NetX Secure TLS module.</span></span> <span data-ttu-id="d8319-321">Musi zostać wywołana przed uzyskaniem dostępu do innych zabezpieczonych usług NetX.</span><span class="sxs-lookup"><span data-stu-id="d8319-321">It must be called before other NetX Secure services can be accessed.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-322">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-322">Parameters</span></span>

<span data-ttu-id="d8319-323">Brak</span><span class="sxs-lookup"><span data-stu-id="d8319-323">None</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-324">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-324">Return Values</span></span>

<span data-ttu-id="d8319-325">Brak</span><span class="sxs-lookup"><span data-stu-id="d8319-325">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-326">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-326">Allowed From</span></span>

<span data-ttu-id="d8319-327">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-327">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-328">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-328">Example</span></span>

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a><span data-ttu-id="d8319-329">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-329">See Also</span></span>

- <span data-ttu-id="d8319-330">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-330">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_local_certificate_add"></a><span data-ttu-id="d8319-331">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-331">nx_secure_tls_local_certificate_add</span></span>

<span data-ttu-id="d8319-332">Dodawanie certyfikatu lokalnego do NetX bezpiecznej sesji protokołu TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-332">Add a local certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-333">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-333">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="d8319-334">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-334">Description</span></span>

<span data-ttu-id="d8319-335">Ta usługa dodaje zainicjowane wystąpienie struktury NX_SECURE_X509_CERT do lokalnego magazynu sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-335">This service adds an initialized NX_SECURE_X509_CERT structure instance to the local store of a TLS session.</span></span> <span data-ttu-id="d8319-336">Ten certyfikat może być używany przez stos TLS do identyfikowania urządzenia podczas uzgadniania TLS (jeśli został oznaczony jako certyfikat tożsamości podczas inicjowania struktury certyfikatu przy użyciu nx_secure_x509_certificate_initialize) lub jako wystawca w ramach łańcucha certyfikatów dostarczonego do hosta zdalnego podczas uzgadniania protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-336">This certificate may used by the TLS stack to identify the device during the TLS handshake (if it was marked as an identity certificate during initialization of the certificate structure using nx_secure_x509_certificate_initialize), or as an issuer as part of a certificate chain provided to the remote host during the TLS handshake.</span></span>

<span data-ttu-id="d8319-337">Jeśli potrzebujesz wielu certyfikatów lokalnych o tej samej nazwie pospolitej, certyfikaty mogą być dodawane za pomocą usługi *nx_secure_tls_server_certificate_add* (Zobacz ostrzeżenie poniżej).</span><span class="sxs-lookup"><span data-stu-id="d8319-337">If multiple local certificates with the same Common Name are needed, certificates may be added using the *nx_secure_tls_server_certificate_add* service (see warning below).</span></span>

<span data-ttu-id="d8319-338">**Wymagany** jest certyfikat w trybie serwera TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-338">A certificate is **required** for TLS Server mode.</span></span>

<span data-ttu-id="d8319-339">Certyfikat jest *opcjonalny* dla trybu klienta protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-339">A certificate is *optional* for TLS Client mode.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8319-340">*Ten interfejs API nie powinien być używany z tą samą sesją TLS podczas korzystania z nx_secure_tls_server_certificate_add. Interfejs API certyfikatu serwera używa unikatowego identyfikatora liczbowego dla każdego certyfikatu, a nx_secure_tls_local_certificate_add indeksy na podstawie nazwy pospolitej X. 509. Lokalne usługi certyfikatów zapewniają wygodną alternatywę dla identyfikatora liczbowego dla aplikacji, które używają tylko jednego certyfikatu tożsamości — przy użyciu nazwy pospolitej aplikacja nie musi śledzić identyfikatorów liczbowych.*</span><span class="sxs-lookup"><span data-stu-id="d8319-340">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-341">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-341">Parameters</span></span>

- <span data-ttu-id="d8319-342">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-342">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="d8319-343">**certificate_ptr** Wskaźnik do zainicjowane wystąpienie certyfikatu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-343">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-344">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-344">Return Values</span></span>

- <span data-ttu-id="d8319-345">**NX_SUCCESS** (0X00) pomyślne dodanie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-345">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="d8319-346">W **NX_INVALID_PARAMETERS** (0x4D) podjęto próbę dodania nieprawidłowego lub zduplikowanego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-346">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid or duplicate certificate.</span></span>
- <span data-ttu-id="d8319-347">**NX_PTR_ERROR** (0X07) Nieprawidłowa sesja protokołu TLS lub wskaźnik certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-347">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-348">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-348">Allowed From</span></span>

<span data-ttu-id="d8319-349">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-350">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-350">Example</span></span>

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-351">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-351">See Also</span></span>

- <span data-ttu-id="d8319-352">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-352">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-353">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-353">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-354">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-354">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-355">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="d8319-355">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="d8319-356">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="d8319-356">nx_secure_tls_local_certificate_find</span></span>

## <a name="nx_secure_tls_local_certificate_find"></a><span data-ttu-id="d8319-357">nx_secure_tls_local_certificate_find</span><span class="sxs-lookup"><span data-stu-id="d8319-357">nx_secure_tls_local_certificate_find</span></span>

<span data-ttu-id="d8319-358">Znajdowanie certyfikatu lokalnego w NetX bezpiecznej sesji TLS według nazwy pospolitej</span><span class="sxs-lookup"><span data-stu-id="d8319-358">Find a local certificate in a NetX Secure TLS Session by Common Name</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-359">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-359">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a><span data-ttu-id="d8319-360">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-360">Description</span></span>

<span data-ttu-id="d8319-361">Ta usługa umożliwia znalezienie certyfikatu w magazynie certyfikatów urządzeń lokalnych sesji TLS i zwrócenie wskaźnika do struktury NX_SECURE_X509_CERT w sklepie.</span><span class="sxs-lookup"><span data-stu-id="d8319-361">This service finds a certificate in the local device certificate store of a TLS session and returns a pointer to the NX_SECURE_X509_CERT structure in the store.</span></span> <span data-ttu-id="d8319-362">Parametr common_name i jego długość (name_length) służą do identyfikowania certyfikatu w magazynie przez dopasowanie pola nazwy pospolitej tematu dla certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="d8319-362">The common_name parameter and it's length (name_length) are used to identify the certificate in the store by matching the certificate's X.509 Subject Common Name field.</span></span>

<span data-ttu-id="d8319-363">Jeśli istnieje więcej niż jeden certyfikat o tej samej nazwie pospolitej, tylko pierwszy z nich zostanie zwrócony — zamiast tego użyj *nx_secure_tls_server_certificate_find* .</span><span class="sxs-lookup"><span data-stu-id="d8319-363">If more than one certificate with the same Common Name is present, only the first one will be returned – use *nx_secure_tls_server_certificate_find* instead.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8319-364">*Ten interfejs API nie powinien być używany z tą samą sesją TLS podczas korzystania z nx_secure_tls_server_certificate_add. Interfejs API certyfikatu serwera używa unikatowego identyfikatora liczbowego dla każdego certyfikatu, a nx_secure_tls_local_certificate_add indeksy na podstawie nazwy pospolitej X. 509. Lokalne usługi certyfikatów zapewniają wygodną alternatywę dla identyfikatora liczbowego dla aplikacji, które używają tylko jednego certyfikatu tożsamości — przy użyciu nazwy pospolitej aplikacja nie musi śledzić identyfikatorów liczbowych.*</span><span class="sxs-lookup"><span data-stu-id="d8319-364">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-365">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-365">Parameters</span></span>

- <span data-ttu-id="d8319-366">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-366">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="d8319-367">**certyfikat** Zwróć wskaźnik do zgodnego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-367">**certificate** Return Pointer to matched certificate.</span></span>
- <span data-ttu-id="d8319-368">**common_name** Nazwa pospolita do dopasowania (nazwa DNS).</span><span class="sxs-lookup"><span data-stu-id="d8319-368">**common_name** Common Name string to match (DNS name).</span></span>
- <span data-ttu-id="d8319-369">**name_length** Długość common_name danych ciągu.</span><span class="sxs-lookup"><span data-stu-id="d8319-369">**name_length** Length of common_name string data.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-370">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-370">Return Values</span></span>

- <span data-ttu-id="d8319-371">Znaleziono certyfikat **NX_SUCCESS** (0x00) i wskaźnik został zwrócony w parametrze "Certificate".</span><span class="sxs-lookup"><span data-stu-id="d8319-371">**NX_SUCCESS** (0x00) Certificate was found and pointer returned in "certificate" parameter.</span></span>
- <span data-ttu-id="d8319-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0X119) nie znaleziono certyfikatu o podanej nazwie pospolitej.</span><span class="sxs-lookup"><span data-stu-id="d8319-372">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) No certificate with the supplied Common Name was found.</span></span>
- <span data-ttu-id="d8319-373">**NX_PTR_ERROR** (0X07) Nieprawidłowa sesja TLS, wskaźnik certyfikatu lub ciąg nazwy pospolitej.</span><span class="sxs-lookup"><span data-stu-id="d8319-373">**NX_PTR_ERROR** (0x07) Invalid TLS session, certificate pointer, or common name string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-374">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-374">Allowed From</span></span>

<span data-ttu-id="d8319-375">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-376">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-376">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate_ptr;

/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */

status = nx_secure_tls_local_certificate_find(&tls_session, &certificate_ptr,
                                      “common name”, strlen(“common name”));

/* If status is NX_SUCCESS the variable “certificate_ptr” points to a certificate
   structure containing a certificate with the Common Name “common name”. */
```

### <a name="see-also"></a><span data-ttu-id="d8319-377">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-377">See Also</span></span>

- <span data-ttu-id="d8319-378">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-378">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-379">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-379">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-380">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-380">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-381">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="d8319-381">nx_secure_tls_local_certificate_remove</span></span>
- <span data-ttu-id="d8319-382">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-382">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_local_certificate_remove"></a><span data-ttu-id="d8319-383">nx_secure_tls_local_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="d8319-383">nx_secure_tls_local_certificate_remove</span></span>

<span data-ttu-id="d8319-384">Usuń certyfikat lokalny z bezpiecznej sesji protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-384">Remove local certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-385">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-385">Prototype</span></span>

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a><span data-ttu-id="d8319-386">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-386">Description</span></span>

<span data-ttu-id="d8319-387">Ta usługa usuwa wystąpienie certyfikatu lokalnego z sesji TLS, które zostało podżądane dla pola Nazwa pospolita w certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="d8319-387">This service removes a local certificate instance from a TLS session, keyed on the Common Name field in the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8319-388">*Ten interfejs API nie powinien być używany z tą samą sesją TLS podczas korzystania z nx_secure_tls_server_certificate_add. Interfejs API certyfikatu serwera używa unikatowego identyfikatora liczbowego dla każdego certyfikatu, a nx_secure_tls_local_certificate_add indeksy na podstawie nazwy pospolitej X. 509. Lokalne usługi certyfikatów zapewniają wygodną alternatywę dla identyfikatora liczbowego dla aplikacji, które używają tylko jednego certyfikatu tożsamości — przy użyciu nazwy pospolitej aplikacja nie musi śledzić identyfikatorów liczbowych.*</span><span class="sxs-lookup"><span data-stu-id="d8319-388">*This API should not be used with the same TLS session when using nx_secure_tls_server_certificate_add. The server certificate API uses a unique numeric identifier for each certificate, and nx_secure_tls_local_certificate_add indexes based on the X.509 Common Name. The local certificate services provide a convenient alternative to the numeric identifier for applications that use only a single identity certificate – by using the Common Name, the application need not keep track of numeric identifiers.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-389">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-389">Parameters</span></span>

- <span data-ttu-id="d8319-390">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-390">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="d8319-391">**common_name** Wartość nazwy pospolitej certyfikatu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="d8319-391">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="d8319-392">**common_name_length** Długość ciągu nazwy pospolitej.</span><span class="sxs-lookup"><span data-stu-id="d8319-392">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-393">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-393">Return Values</span></span>

- <span data-ttu-id="d8319-394">**NX_SUCCESS** (0X00) pomyślne dodanie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-394">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="d8319-395">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-395">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="d8319-396">Nie znaleziono certyfikatu **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119).</span><span class="sxs-lookup"><span data-stu-id="d8319-396">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-397">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-397">Allowed From</span></span>

<span data-ttu-id="d8319-398">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-399">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-399">Example</span></span>

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-400">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-400">See Also</span></span>

- <span data-ttu-id="d8319-401">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-401">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-402">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-402">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-403">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-403">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-404">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-404">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_metadata_size_calculate"></a><span data-ttu-id="d8319-405">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="d8319-405">nx_secure_tls_metadata_size_calculate</span></span>

<span data-ttu-id="d8319-406">Obliczanie rozmiaru metadanych kryptograficznych dla sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-406">Calculate size of cryptographic metadata for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-407">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-407">Prototype</span></span>

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a><span data-ttu-id="d8319-408">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-408">Description</span></span>

<span data-ttu-id="d8319-409">Ta usługa oblicza i zwraca rozmiar metadanych kryptograficznych wymaganych dla określonej sesji TLS i tabeli kryptografii TLS (zobacz sekcję "Inicjowanie protokołu TLS z metodami kryptograficznymi", aby uzyskać więcej informacji na temat tabeli szyfrowania kryptograficznego).</span><span class="sxs-lookup"><span data-stu-id="d8319-409">This service calculates and returns the size of the cryptographic metadata needed for a particular TLS session and TLS cryptography table (see the section "Initializing TLS with Cryptographic Methods" for more information on the cryptographic cipher table).</span></span>

<span data-ttu-id="d8319-410">Ta usługa powinna zostać wywołana z żądaną tabelą kryptograficzną, aby obliczyć rozmiar buforu metadanych przekazaną do nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="d8319-410">This service should be called with the desired cryptographic table to calculate the size of the metadata buffer passed into nx_secure_tls_session_create.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-411">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-411">Parameters</span></span>

- <span data-ttu-id="d8319-412">**crypto_table** Wskaźnik do kompletnej tabeli kryptografii Secure TLS NetX.</span><span class="sxs-lookup"><span data-stu-id="d8319-412">**crypto_table** Pointer to a complete NetX Secure TLS cryptography table.</span></span>
- <span data-ttu-id="d8319-413">**metadata_size** Dane wyjściowe obliczeń rozmiaru w bajtach.</span><span class="sxs-lookup"><span data-stu-id="d8319-413">**metadata_size** The output of the size calculation in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-414">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-414">Return Values</span></span>

- <span data-ttu-id="d8319-415">**NX_SUCCESS** (0X00) pomyślnie obliczyć rozmiar metadanych.</span><span class="sxs-lookup"><span data-stu-id="d8319-415">**NX_SUCCESS** (0x00) Successful calculation of metadata size.</span></span>
- <span data-ttu-id="d8319-416">**NX_PTR_ERROR** (0X07) Nieprawidłowa tabela kryptograficzna lub wskaźnik zwracanego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="d8319-416">**NX_PTR_ERROR** (0x07) Invalid crypto table or return size pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-417">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-417">Allowed From</span></span>

<span data-ttu-id="d8319-418">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-418">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-419">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-419">Example</span></span>

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Return variable for metadata size. */
ULONG crypto_metadata_size;

/* Calculate metadata size.  */
status =  nx_secure_tls_metadata_size_calculate(&nx_crypto_tls_ciphers,
                                                &crypto_metadata_size);


/* If status is NX_SUCCESS then crypto_metadata_size contains the size of the
   metadata buffer for the table nx_crypto_tls_ciphers.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-420">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-420">See Also</span></span>

- <span data-ttu-id="d8319-421">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-421">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_module_hash_compute"></a><span data-ttu-id="d8319-422">nx_secure_module_hash_compute</span><span class="sxs-lookup"><span data-stu-id="d8319-422">nx_secure_module_hash_compute</span></span>

<span data-ttu-id="d8319-423">Oblicz wartość skrótu procedur NetX Secure Library</span><span class="sxs-lookup"><span data-stu-id="d8319-423">Compute the hash value of the NetX Secure library routines</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-424">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-424">Prototype</span></span>

```C
VOID nx_secure_module_hash_compute(VOID);
```

### <a name="description"></a><span data-ttu-id="d8319-425">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-425">Description</span></span>

<span data-ttu-id="d8319-426">Ta usługa Inicjuje moduł bezpiecznego protokołu TLS NetX.</span><span class="sxs-lookup"><span data-stu-id="d8319-426">This service initializes the NetX Secure TLS module.</span></span> <span data-ttu-id="d8319-427">Musi zostać wywołana przed uzyskaniem dostępu do innych zabezpieczonych usług NetX.</span><span class="sxs-lookup"><span data-stu-id="d8319-427">It must be called before other NetX Secure services can be accessed.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-428">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-428">Parameters</span></span>

<span data-ttu-id="d8319-429">Brak</span><span class="sxs-lookup"><span data-stu-id="d8319-429">None</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-430">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-430">Return Values</span></span>

<span data-ttu-id="d8319-431">Brak</span><span class="sxs-lookup"><span data-stu-id="d8319-431">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-432">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-432">Allowed From</span></span>

<span data-ttu-id="d8319-433">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-433">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-434">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-434">Example</span></span>

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a><span data-ttu-id="d8319-435">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-435">See Also</span></span>

- <span data-ttu-id="d8319-436">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-436">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_packet_allocate"></a><span data-ttu-id="d8319-437">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-437">nx_secure_tls_packet_allocate</span></span>

<span data-ttu-id="d8319-438">Przydziel pakiet dla sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-438">Allocate a packet for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-439">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-439">Prototype</span></span>

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d8319-440">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-440">Description</span></span>

<span data-ttu-id="d8319-441">Ta usługa przydziela NX_PACKET dla określonej aktywnej sesji protokołu TLS z określonego NX_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="d8319-441">This service allocates an NX_PACKET for the specified active TLS session from the specified NX_PACKET_POOL.</span></span> <span data-ttu-id="d8319-442">Ta usługa powinna być wywoływana przez aplikację w celu przydzielenia pakietów danych do wysłania przez połączenie TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-442">This service should be called by the application to allocate data packets to be sent over a TLS connection.</span></span> <span data-ttu-id="d8319-443">Sesja TLS musi zostać zainicjowana przed wywołaniem tej usługi.</span><span class="sxs-lookup"><span data-stu-id="d8319-443">The TLS session must be initialized before calling this service.</span></span>

<span data-ttu-id="d8319-444">Przydzielony pakiet jest prawidłowo zainicjowany, aby dane nagłówka i stopki TLS mogły zostać dodane po wypełnieniu danych pakietu.</span><span class="sxs-lookup"><span data-stu-id="d8319-444">The allocated packet is properly initialized so that TLS header and footer data may be added after the packet data is populated.</span></span> <span data-ttu-id="d8319-445">Zachowanie jest takie samo jak *nx_packet_allocate*.</span><span class="sxs-lookup"><span data-stu-id="d8319-445">The behavior is otherwise identical to *nx_packet_allocate*.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-446">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-446">Parameters</span></span>

- <span data-ttu-id="d8319-447">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-447">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="d8319-448">**pool_ptr** Wskaźnik do NX_PACKET_POOL, z którego ma zostać przydzielony pakiet.</span><span class="sxs-lookup"><span data-stu-id="d8319-448">**pool_ptr** Pointer to an NX_PACKET_POOL from which to allocate the packet.</span></span>
- <span data-ttu-id="d8319-449">**packet_ptr** Wskaźnik wyjściowy do nowo przydzielonych pakietów.</span><span class="sxs-lookup"><span data-stu-id="d8319-449">**packet_ptr** Output pointer to the newly-allocated packet.</span></span>
- <span data-ttu-id="d8319-450">**WAIT_OPTION** Opcja zawieszenia dla przydziału pakietu.</span><span class="sxs-lookup"><span data-stu-id="d8319-450">**wait_option** Suspension option for packet allocation.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-451">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-451">Return Values</span></span>

- <span data-ttu-id="d8319-452">Pomyślna alokacja pakietu **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="d8319-452">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="d8319-453">Alokacja podstawowego pakietu **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="d8319-453">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>
- <span data-ttu-id="d8319-454">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) dostarczona sesja TLS nie została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="d8319-454">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-455">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-455">Allowed From</span></span>

<span data-ttu-id="d8319-456">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-456">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-457">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-457">Example</span></span>

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-458">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-458">See Also</span></span>

- <span data-ttu-id="d8319-459">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-459">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="d8319-460">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-460">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-461">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-461">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-462">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-462">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-463">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="d8319-463">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="d8319-464">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-464">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="d8319-465">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="d8319-465">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="d8319-466">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="d8319-466">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="d8319-467">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-467">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_psk_add"></a><span data-ttu-id="d8319-468">nx_secure_tls_psk_add</span><span class="sxs-lookup"><span data-stu-id="d8319-468">nx_secure_tls_psk_add</span></span>

<span data-ttu-id="d8319-469">Dodaj klucz wstępny do NetX bezpiecznej sesji TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-469">Add a Pre-Shared Key to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-470">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-470">Prototype</span></span>

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a><span data-ttu-id="d8319-471">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-471">Description</span></span>

<span data-ttu-id="d8319-472">Ta usługa dodaje klucz wstępny (PSK), jego ciąg tożsamości i wskazówkę dotyczącą tożsamości do bloku kontroli sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-472">This service adds a Pre-Shared Key (PSK), its identity string, and an identity hint to a TLS Session control block.</span></span> <span data-ttu-id="d8319-473">PSK jest używany zamiast certyfikatu cyfrowego, gdy ciphersuites PSK są włączone i używane.</span><span class="sxs-lookup"><span data-stu-id="d8319-473">The PSK is used in place of a digital certificate when PSK ciphersuites are enabled and used.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-474">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-474">Parameters</span></span>

- <span data-ttu-id="d8319-475">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-475">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="d8319-476">**pre_shared_key** Rzeczywista wartość klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="d8319-476">**pre_shared_key** The actual PSK value.</span></span>
- <span data-ttu-id="d8319-477">**psk_length** Długość wartości klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="d8319-477">**psk_length** The length of the PSK value.</span></span>
- <span data-ttu-id="d8319-478">**psk_identity** Ciąg służący do identyfikowania tej wartości PSK.</span><span class="sxs-lookup"><span data-stu-id="d8319-478">**psk_identity** A string used to identify this PSK value.</span></span>
- <span data-ttu-id="d8319-479">**identity_length** Długość tożsamości PSK.</span><span class="sxs-lookup"><span data-stu-id="d8319-479">**identity_length** The length of the PSK identity.</span></span>
- <span data-ttu-id="d8319-480">**Wskazówka** Ciąg używany do wskazania grupy PSKs do wyboru na serwerze TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-480">**hint** A string used to indicate which group of PSKs to choose from on a TLS server.</span></span>
- <span data-ttu-id="d8319-481">**hint_length** Długość ciągu wskazówki.</span><span class="sxs-lookup"><span data-stu-id="d8319-481">**hint_length** The length of the hint string.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-482">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-482">Return Values</span></span>

- <span data-ttu-id="d8319-483">**NX_SUCCESS** (0X00) pomyślne dodanie klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="d8319-483">**NX_SUCCESS** (0x00) Successful addition of PSK.</span></span>
- <span data-ttu-id="d8319-484">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-484">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="d8319-485">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0X125) nie może dodać innego klucza PSK.</span><span class="sxs-lookup"><span data-stu-id="d8319-485">**NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125)  Cannot add another PSK.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-486">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-486">Allowed From</span></span>

<span data-ttu-id="d8319-487">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-487">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-488">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-488">Example</span></span>

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-489">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-489">See Also</span></span>

- <span data-ttu-id="d8319-490">nx_secure_tls_client_psk_set</span><span class="sxs-lookup"><span data-stu-id="d8319-490">nx_secure_tls_client_psk_set</span></span>
- <span data-ttu-id="d8319-491">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-491">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-492">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-492">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-493">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-493">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-494">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-494">nx_secure_tls_local_certificate_add</span></span>

## <a name="nx_secure_tls_remote_certificate_allocate"></a><span data-ttu-id="d8319-495">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-495">nx_secure_tls_remote_certificate_allocate</span></span>

<span data-ttu-id="d8319-496">Przydzielanie miejsca dla certyfikatu dostarczonego przez hosta zdalnego protokołu TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-496">Allocate space for the certificate provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-497">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-497">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a><span data-ttu-id="d8319-498">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-498">Description</span></span>

<span data-ttu-id="d8319-499">Ta usługa dodaje niezainicjowane wystąpienie struktury NX_SECURE_X509_CERT do sesji protokołu TLS w celu przydzielenia miejsca dla certyfikatów dostarczonych przez hosta zdalnego podczas sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-499">This service adds an uninitialized NX_SECURE_X509_CERT structure instance to a TLS session for the purpose of allocating space for certificates provided by a remote host during a TLS session.</span></span> <span data-ttu-id="d8319-500">Dane certyfikatu zdalnego są analizowane przez NetX Secure TLS i te informacje są używane do wypełniania wystąpienia struktury certyfikatu przekazanego do tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d8319-500">The remote certificate data is parsed by NetX Secure TLS and that information is used to populate the certificate structure instance provided to this function.</span></span> <span data-ttu-id="d8319-501">Certyfikaty dodane w ten sposób są umieszczane na liście połączonej.</span><span class="sxs-lookup"><span data-stu-id="d8319-501">Certificates added in this manner are placed in a linked list.</span></span>

<span data-ttu-id="d8319-502">Jeśli oczekujesz, że host zdalny udostępni wiele certyfikatów, ta funkcja powinna być wywoływana wielokrotnie w celu przydzielenia miejsca dla wszystkich certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d8319-502">If it is expected that the remote host will provide multiple certificates, this function should be called repeatedly to allocate space for all certificates.</span></span> <span data-ttu-id="d8319-503">Dodatkowe certyfikaty są dodawane na końcu listy połączonej z certyfikatem.</span><span class="sxs-lookup"><span data-stu-id="d8319-503">The additional certificates are added to the end of the certificate linked list.</span></span>

<span data-ttu-id="d8319-504">Niepowodzenie przydzielenia certyfikatu zdalnego spowoduje niepowodzenie trybu klienta protokołu TLS w trakcie uzgadniania TLS, chyba że jest używany klucz wstępny (PSK) ciphersuite.</span><span class="sxs-lookup"><span data-stu-id="d8319-504">Failure to allocate a remote certificate will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="d8319-505">Parametr *raw_certificate_buffer* wskazuje miejsce przydzielenia do przechowywania przychodzącego certyfikatu zdalnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-505">The *raw_certificate_buffer* parameter points to space allocated to store the incoming remote certificate.</span></span> <span data-ttu-id="d8319-506">Typowe certyfikaty z kluczami RSA 2048 bitów przy użyciu algorytmu SHA-256 są w zakresie od 1000-2000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="d8319-506">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="d8319-507">Bufor powinien być wystarczająco duży, aby zmniejszyć rozmiar, ale w zależności od tego, czy certyfikaty hosta zdalnego mogą być znacznie mniejsze lub większe.</span><span class="sxs-lookup"><span data-stu-id="d8319-507">The buffer should be large enough to at least hold that size, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="d8319-508">Należy pamiętać, że jeśli bufor jest za mały, aby pomieścić certyfikat przychodzący, uzgadnianie TLS zakończy się błędem.</span><span class="sxs-lookup"><span data-stu-id="d8319-508">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

<span data-ttu-id="d8319-509">W przypadku trybu serwera TLS niezbędna jest alokacja certyfikatu zdalnego tylko wtedy, gdy jest włączone uwierzytelnianie certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="d8319-509">For TLS Server mode, a remote certificate allocation is needed only if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-510">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-510">Parameters</span></span>

- <span data-ttu-id="d8319-511">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-511">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="d8319-512">**certificate_ptr** Wskaźnik do niezainicjowanego wystąpienia certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="d8319-512">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="d8319-513">**raw_certificate_buffer** Wskaźnik do bufora, aby przechowywać nieanalizowany certyfikat otrzymany z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-513">**raw_certificate_buffer** Pointer to a buffer to hold the un-parsed certificate received from the remote host.</span></span>
- <span data-ttu-id="d8319-514">**raw_buffer_size** Rozmiar nieprzetworzonego bufora certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d8319-514">**raw_buffer_size** Size of the raw certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-515">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-515">Return Values</span></span>

- <span data-ttu-id="d8319-516">**NX_SUCCESS** (0X00) pomyślne przypisanie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-516">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="d8319-517">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-517">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="d8319-518">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) dostarczony bufor jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="d8319-518">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="d8319-519">**NX_INVALID_PARAMETERS** (0x4D) próbował dodać nieprawidłowy certyfikat.</span><span class="sxs-lookup"><span data-stu-id="d8319-519">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-520">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-520">Allowed From</span></span>

<span data-ttu-id="d8319-521">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-521">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-522">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-522">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-523">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-523">See Also</span></span>

- <span data-ttu-id="d8319-524">nx_secure_x509_certificate_initialize,</span><span class="sxs-lookup"><span data-stu-id="d8319-524">nx_secure_x509_certificate_initialize,</span></span>
- <span data-ttu-id="d8319-525">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-525">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a><span data-ttu-id="d8319-526">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-526">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

<span data-ttu-id="d8319-527">Przydzielanie miejsca dla wszystkich certyfikatów dostarczonych przez zdalnego hosta protokołu TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-527">Allocate space for all certificates provided by a remote TLS host</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-528">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-528">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="d8319-529">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-529">Description</span></span>

<span data-ttu-id="d8319-530">Ta usługa przydziela miejsce do przetwarzania łańcuchów certyfikatów przychodzących z hostów serwera zdalnego w celu przeprowadzenia uwierzytelniania X. 509 i weryfikacji w wystąpieniu klienta TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-530">This service allocates space to process incoming certificate chains from remote server hosts in order to perform X.509 authentication and verification in a TLS Client instance.</span></span> <span data-ttu-id="d8319-531">W przypadku trybu serwera TLS, alokacja certyfikatów zdalnych jest wymagana tylko wtedy, gdy jest włączone uwierzytelnianie certyfikatu X. 509 w przypadku serwera TLS, zamiast tego należy użyć *nx_secure_tls_session_x509_client_verify_configure* usługi.</span><span class="sxs-lookup"><span data-stu-id="d8319-531">For TLS Server mode, remote certificate allocation is needed only if client X.509 certificate authentication is enabled – for TLS Server instances the service *nx_secure_tls_session_x509_client_verify_configure* should be used instead.</span></span>

<span data-ttu-id="d8319-532">Niepowodzenie przydzielenia certyfikatów zdalnych spowoduje niepowodzenie trybu klienta protokołu TLS w trakcie uzgadniania TLS, chyba że jest używany klucz wstępny (PSK) ciphersuite.</span><span class="sxs-lookup"><span data-stu-id="d8319-532">Failure to allocate remote certificates will cause TLS Client mode to fail during the TLS handshake unless a Pre-Shared Key (PSK) ciphersuite is in use.</span></span>

<span data-ttu-id="d8319-533">Parametr *certificate_buffer* wskazuje miejsce przydzielenia do przechowywania przychodzących certyfikatów zdalnych i bloków sterowania wymaganych przez te certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="d8319-533">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="d8319-534">Bufor zostanie podzielony przez liczbę certyfikatów (*certs_number*) o równej części danego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-534">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="d8319-535">Parametr *buffer_size*  wskazuje rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="d8319-535">The *buffer_size*  parameter indicates the size of the buffer.</span></span> <span data-ttu-id="d8319-536">Wymaganą ilość miejsca można znaleźć za pomocą następującej formuły:</span><span class="sxs-lookup"><span data-stu-id="d8319-536">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="d8319-537">Typowe certyfikaty z kluczami RSA 2048 bitów przy użyciu algorytmu SHA-256 są w zakresie od 1000-2000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="d8319-537">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="d8319-538">Bufor powinien być wystarczająco duży, aby zmniejszyć rozmiar każdego certyfikatu, ale w zależności od tego, czy certyfikaty hosta zdalnego mogą być znacznie mniejsze lub większe.</span><span class="sxs-lookup"><span data-stu-id="d8319-538">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="d8319-539">Należy pamiętać, że jeśli bufor jest za mały, aby pomieścić certyfikat przychodzący, uzgadnianie TLS zakończy się błędem.</span><span class="sxs-lookup"><span data-stu-id="d8319-539">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-540">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-540">Parameters</span></span>

- <span data-ttu-id="d8319-541">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-541">**session_ptr** Pointer to a previously created TLS Session  instance.</span></span>
- <span data-ttu-id="d8319-542">**certs_number** Liczba certyfikatów do przydzielenia z podanego buforu.</span><span class="sxs-lookup"><span data-stu-id="d8319-542">**certs_number** Number of certificates to allocate from the  provided buffer.</span></span>
- <span data-ttu-id="d8319-543">**certificate_buffer** Wskaźnik do buforu w celu przechowywania certyfikatów odebranych z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-543">**certificate_buffer** Pointer to a buffer to hold certificates received  from a remote host.</span></span>
- <span data-ttu-id="d8319-544">**buffer_size** Rozmiar buforu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-544">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-545">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-545">Return Values</span></span>

- <span data-ttu-id="d8319-546">**NX_SUCCESS** (0X00) pomyślne przypisanie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-546">**NX_SUCCESS** (0x00) Successful allocation of certificate.</span></span>
- <span data-ttu-id="d8319-547">**NX_PTR_ERROR** (0X07) Nieprawidłowa sesja protokołu TLS lub wskaźnik buforu.</span><span class="sxs-lookup"><span data-stu-id="d8319-547">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="d8319-548">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) dostarczony bufor jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="d8319-548">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="d8319-549">**NX_INVALID_PARAMETERS** (0x4D) bufor był zbyt mały, aby pomieścić żądaną liczbę certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d8319-549">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold  the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-550">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-550">Allowed From</span></span>

<span data-ttu-id="d8319-551">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-551">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-552">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-552">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE           (CERTIFICATE_NUMBER * \
                              (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_buffer_allocate(&tls_session,
                                                      CERTIFICATE_NUMBER,
                                                      certificate_buffer,
                                                      BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-553">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-553">See Also</span></span>

- <span data-ttu-id="d8319-554">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-554">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-555">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-555">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_remote_certificate_free_all"></a><span data-ttu-id="d8319-556">nx_secure_tls_remote_certificate_free_all</span><span class="sxs-lookup"><span data-stu-id="d8319-556">nx_secure_tls_remote_certificate_free_all</span></span>

<span data-ttu-id="d8319-557">Wolne miejsce przydzielono dla certyfikatów przychodzących</span><span class="sxs-lookup"><span data-stu-id="d8319-557">Free space allocated for incoming certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-558">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-558">Prototype</span></span>

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="d8319-559">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-559">Description</span></span>

<span data-ttu-id="d8319-560">Ta usługa służy do zwalniania wszystkich buforów certyfikatów przypisywanych do określonej sesji TLS przez nx_secure_tls_remote_certificate_allocated, zwracając je do wolnego obszaru certyfikatu tej sesji.</span><span class="sxs-lookup"><span data-stu-id="d8319-560">This service is used to free all of the certificate buffers allocated to a particular TLS Session by nx_secure_tls_remote_certificate_allocated by returning them to that session's free certificate space.</span></span> <span data-ttu-id="d8319-561">Może to być konieczne, jeśli aplikacja ponownie używa obiektu sesji protokołu TLS bez usuwania go i ponownego tworzenia przy użyciu nx_secure_tls_session_delete i nx_secure_tls_session_create.</span><span class="sxs-lookup"><span data-stu-id="d8319-561">This may be necessary if an application reuses a TLS session object without deleting it and recreating it with nx_secure_tls_session_delete and nx_secure_tls_session_create.</span></span>

<span data-ttu-id="d8319-562">Należy pamiętać, że zdalne miejsce na certyfikacie jest automatycznie odzyskiwane w przypadku zresetowania sesji TLS w nx_secure_tls_session_end tak, aby większość aplikacji nie wymagała wywołania tej usługi.</span><span class="sxs-lookup"><span data-stu-id="d8319-562">Note that the remote certificate space is recovered automatically when the TLS session is reset as happens in nx_secure_tls_session_end so most applications should not need to call this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-563">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-563">Parameters</span></span>

- <span data-ttu-id="d8319-564">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-564">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-565">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-565">Return Values</span></span>

- <span data-ttu-id="d8319-566">Operacja powiodła się **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="d8319-566">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="d8319-567">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-567">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="d8319-568">Błąd wewnętrzny **NX_INVALID_PARAMETERS** (0x4D) — magazyn certyfikatów jest niemożliwy do uszkodzenia.</span><span class="sxs-lookup"><span data-stu-id="d8319-568">**NX_INVALID_PARAMETERS** (0x4D) Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-569">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-569">Allowed From</span></span>

<span data-ttu-id="d8319-570">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-570">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-571">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-571">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */

/* … TLS session setup, TCP connection, etc… */

/* End TLS session. */
nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

/* Free up certificate buffers for next connection. */
nx_secure_tls_remote_certificate_free_all(&tls_session);
```

### <a name="see-also"></a><span data-ttu-id="d8319-572">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-572">See Also</span></span>

- <span data-ttu-id="d8319-573">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-573">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-574">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-574">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-575">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-575">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-576">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="d8319-576">nx_secure_tls_session_end</span></span>

## <a name="nx_secure_tls_server_certificate_add"></a><span data-ttu-id="d8319-577">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-577">nx_secure_tls_server_certificate_add</span></span>

<span data-ttu-id="d8319-578">Dodawanie certyfikatu przeznaczonego dla serwerów TLS przy użyciu identyfikatora liczbowego</span><span class="sxs-lookup"><span data-stu-id="d8319-578">Add a certificate specifically for TLS servers using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-579">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-579">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="d8319-580">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-580">Description</span></span>

<span data-ttu-id="d8319-581">Ta usługa służy do dodawania certyfikatu do lokalnego magazynu sesji TLS (zobacz nx_secure_tls_local_certificate_add) przy użyciu identyfikatora liczbowego zamiast indeksowania magazynu przy użyciu tematu X. 509 (nazwa pospolita) w ramach certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-581">This service is used to add a certificate to a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span> <span data-ttu-id="d8319-582">Identyfikator liczbowy jest oddzielony od certyfikatu i umożliwia dodawanie wielu certyfikatów jako certyfikatów tożsamości do serwera TLS, a także Zezwalanie na dodawanie wielu certyfikatów o tej samej nazwie pospolitej do tego samego lokalnego magazynu sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-582">The numeric identifier is separate from the certificate and allows multiple certificates to be added as identity certificates to a TLS server, as well as allowing multiple certificates with the same Common Name to be added to the same TLS session local store.</span></span> <span data-ttu-id="d8319-583">Ta sama usługa może być używana w przypadku certyfikatów klienta, ale jest rzadki, aby klient TLS miał wiele certyfikatów tożsamości.</span><span class="sxs-lookup"><span data-stu-id="d8319-583">This same service can be used for client certificates, but it is rare for a TLS client to have multiple identity certificates.</span></span>

<span data-ttu-id="d8319-584">Parametr cert_id jest niezerową liczbą całkowitą, która jest przypisana przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="d8319-584">The cert_id parameter is a non-zero positive integer assigned by the application.</span></span> <span data-ttu-id="d8319-585">Rzeczywista wartość nie ma znaczenia (inne niż zero), ale musi być unikatowa w magazynie dla podanej sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-585">The actual value does not matter (other than zero) but it must be unique in the store for the provided TLS session.</span></span> <span data-ttu-id="d8319-586">Wartość cert_id może służyć do znajdowania i usuwania certyfikatów z lokalnego magazynu przy użyciu odpowiednio nx_secure_tls_server_certificate_find i nx_secure_tls_server_certificate_remove.</span><span class="sxs-lookup"><span data-stu-id="d8319-586">The cert_id value can be used to find and remove certificates from the local store using nx_secure_tls_server_certificate_find and nx_secure_tls_server_certificate_remove, respectively.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8319-587">*Ten interfejs API nie powinien być używany z tą samą sesją TLS podczas korzystania z nx_secure_tls_local_certificate_add. Interfejs API nx_secure_tls_server_certificate_add używa unikatowego identyfikatora liczbowego dla każdego certyfikatu oraz lokalnego indeksu usług certyfikatów na podstawie nazwy pospolitej X. 509. Usługi certyfikatów serwera umożliwiają istnienie wielu certyfikatów z danymi udostępnionymi (szczególnie nazwa pospolita) w tym samym magazynie lokalnym — jest to przydatne w przypadku serwera z wieloma tożsamościami.*</span><span class="sxs-lookup"><span data-stu-id="d8319-587">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-588">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-588">Parameters</span></span>

- <span data-ttu-id="d8319-589">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-589">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="d8319-590">**certyfikat** Wskaźnik do wcześniej zainicjowanego wystąpienia certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="d8319-590">**certificate** Pointer to a previously initialized X.509 certificate instance.</span></span>
- <span data-ttu-id="d8319-591">**Cert_ID** Dodatni, niezerowy, relatywnie unikatowy numer IDENTYFIKACYJNy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-591">**cert_id** Positive, non-zero, relatively unique certificate ID number.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-592">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-592">Return Values</span></span>

- <span data-ttu-id="d8319-593">Operacja powiodła się **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="d8319-593">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="d8319-594">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik ORCERTIFICATE sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-594">**NX_PTR_ERROR** (0x07) Invalid TLS session orcertificate pointer.</span></span>
- <span data-ttu-id="d8319-595">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) podany identyfikator certyfikatu ma nieprawidłową wartość (najkorzystniej wynosi 0).</span><span class="sxs-lookup"><span data-stu-id="d8319-595">**NX_SECURE_TLS_CERT_ID_INVALID** (0x138) The provided certificate ID had An invalid value (likely 0).</span></span>
- <span data-ttu-id="d8319-596">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) podany identyfikator certyfikatu już istnieje w magazynie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="d8319-596">**NX_SECURE_TLS_CERT_ID_DUPLICATE** (0x139) The provided certificate ID was already present in the local store.</span></span>
- <span data-ttu-id="d8319-597">**NX_INVALID_PARAMETERS (0x4D)** Błąd wewnętrzny — magazyn certyfikatów jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="d8319-597">**NX_INVALID_PARAMETERS(0x4D)** Internal error – certificate store likely corrupt.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-598">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-598">Allowed From</span></span>

<span data-ttu-id="d8319-599">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-599">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-600">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-600">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-601">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-601">See Also</span></span>

- <span data-ttu-id="d8319-602">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-602">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-603">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-603">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="d8319-604">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="d8319-604">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="d8319-605">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="d8319-605">nx_secure_tls_server_certificate_find</span></span>
- <span data-ttu-id="d8319-606">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="d8319-606">nx_secure_tls_server_certificate_remove</span></span>

## <a name="nx_secure_tls_server_certificate_find"></a><span data-ttu-id="d8319-607">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="d8319-607">nx_secure_tls_server_certificate_find</span></span>

<span data-ttu-id="d8319-608">Znajdowanie certyfikatu przy użyciu identyfikatora liczbowego</span><span class="sxs-lookup"><span data-stu-id="d8319-608">Find a certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-609">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-609">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="d8319-610">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-610">Description</span></span>

<span data-ttu-id="d8319-611">Ta usługa jest używana do znajdowania certyfikatu w lokalnym magazynie sesji TLS (zobacz nx_secure_tls_local_certificate_add) przy użyciu identyfikatora liczbowego zamiast indeksowania magazynu przy użyciu tematu X. 509 (nazwa pospolita) w certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="d8319-611">This service is used to find a certificate in a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="d8319-612">Cert_id parametr to niezerową dodatnia liczba całkowita przypisana przez aplikację, gdy certyfikat zostanie dodany do lokalnego magazynu sesji TLS przy użyciu nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="d8319-612">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8319-613">*Ten interfejs API nie powinien być używany z tą samą sesją TLS podczas korzystania z nx_secure_tls_local_certificate_add. Interfejs API nx_secure_tls_server_certificate_add używa unikatowego identyfikatora liczbowego dla każdego certyfikatu oraz lokalnego indeksu usług certyfikatów na podstawie nazwy pospolitej X. 509. Usługi certyfikatów serwera umożliwiają istnienie wielu certyfikatów z danymi udostępnionymi (szczególnie nazwa pospolita) w tym samym magazynie lokalnym — jest to przydatne w przypadku serwera z wieloma tożsamościami.*</span><span class="sxs-lookup"><span data-stu-id="d8319-613">*This API should not be used with the same TLS session when using nx_secure_tls_local_certificate_add. The nx_secure_tls_server_certificate_add API uses a unique numeric identifier for each certificate, and local certificate services index based on the X.509 Common Name. The server certificate services allow multiple certificates with shared data (especially Common Name) to exist in the same local store – this is useful for a server with multiple identities.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-614">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-614">Parameters</span></span>

- <span data-ttu-id="d8319-615">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-615">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="d8319-616">**certyfikat** Wskaźnik na wskaźnik certyfikatu X. 509, aby zwrócić odwołanie do znalezionego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-616">**certificate** Pointer to an X.509 certificate pointer to return a reference to the found certificate.</span></span>
- <span data-ttu-id="d8319-617">**Cert_ID** Wartość identyfikatora certyfikatu o wartości innej niż zero.</span><span class="sxs-lookup"><span data-stu-id="d8319-617">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-618">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-618">Return Values</span></span>

- <span data-ttu-id="d8319-619">Operacja powiodła się **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="d8319-619">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="d8319-620">**NX_PTR_ERROR** (0X07) Nieprawidłowa sesja protokołu TLS lub wskaźnik certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-620">**NX_PTR_ERROR** (0x07) Invalid TLS session or certificate pointer.</span></span>
- <span data-ttu-id="d8319-621">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) podany identyfikator certyfikatu nie jest zgodny z żadnym z magazynów lokalnych podanej sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-621">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-622">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-622">Allowed From</span></span>

<span data-ttu-id="d8319-623">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-623">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-624">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-624">Example</span></span>

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-625">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-625">See Also</span></span>

- <span data-ttu-id="d8319-626">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-626">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-627">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-627">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="d8319-628">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="d8319-628">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="d8319-629">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-629">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="d8319-630">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="d8319-630">nx_secure_tls_server_certificate_remove</span></span>

##  <a name="nx_secure_tls_server_certificate_remove"></a><span data-ttu-id="d8319-631">nx_secure_tls_server_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="d8319-631">nx_secure_tls_server_certificate_remove</span></span>

<span data-ttu-id="d8319-632">Usuwanie certyfikatu serwera lokalnego przy użyciu identyfikatora liczbowego</span><span class="sxs-lookup"><span data-stu-id="d8319-632">Remove a local server certificate using a numeric identifier</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-633">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-633">Prototype</span></span>

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a><span data-ttu-id="d8319-634">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-634">Description</span></span>

<span data-ttu-id="d8319-635">Ta usługa służy do usuwania certyfikatu z lokalnego magazynu sesji TLS (zobacz nx_secure_tls_local_certificate_add) przy użyciu identyfikatora liczbowego zamiast indeksowania magazynu przy użyciu tematu X. 509 (nazwa pospolita) w ramach certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-635">This service is used to remove a certificate from a TLS session's local store (see nx_secure_tls_local_certificate_add) using a numeric identifier instead of indexing the store using the X.509 Subject (Common Name) within the certificate.</span></span>

<span data-ttu-id="d8319-636">Cert_id parametr to niezerową dodatnia liczba całkowita przypisana przez aplikację, gdy certyfikat zostanie dodany do lokalnego magazynu sesji TLS przy użyciu nx_secure_tls_server_certificate_add.</span><span class="sxs-lookup"><span data-stu-id="d8319-636">The cert_id parameter is a non-zero positive integer assigned by the application when the certificate is added to the TLS session local store using nx_secure_tls_server_certificate_add.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-637">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-637">Parameters</span></span>

- <span data-ttu-id="d8319-638">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-638">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="d8319-639">**Cert_ID** Wartość identyfikatora certyfikatu o wartości innej niż zero.</span><span class="sxs-lookup"><span data-stu-id="d8319-639">**cert_id** Non-zero positive certificate ID value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-640">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-640">Return Values</span></span>

- <span data-ttu-id="d8319-641">Operacja powiodła się **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="d8319-641">**NX_SUCCESS** (0x00)Successful operation.</span></span>
- <span data-ttu-id="d8319-642">**NX_PTR_ERROR** (0X07) Nieprawidłowa sesja TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-642">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>
- <span data-ttu-id="d8319-643">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) podany identyfikator certyfikatu nie jest zgodny z żadnym z magazynów lokalnych podanej sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-643">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) The provided certificate ID did not match any in the local store of the provided TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-644">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-644">Allowed From</span></span>

<span data-ttu-id="d8319-645">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-645">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-646">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-646">Example</span></span>

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);
/* Use certificate in TLS session, etc… */

/* Remove certificate from TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_remove(&tls_session, 0x12);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-647">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-647">See Also</span></span>

- <span data-ttu-id="d8319-648">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-648">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-649">nx_secure_tls_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-649">nx_secure_tls_local_certificate_add</span></span>
- <span data-ttu-id="d8319-650">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="d8319-650">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="d8319-651">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-651">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="d8319-652">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="d8319-652">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_alert_value_get"></a><span data-ttu-id="d8319-653">nx_secure_tls_session_alert_value_get</span><span class="sxs-lookup"><span data-stu-id="d8319-653">nx_secure_tls_session_alert_value_get</span></span>

<span data-ttu-id="d8319-654">Pobierz wartość i poziom alertu TLS wysyłanego przez hosta zdalnego</span><span class="sxs-lookup"><span data-stu-id="d8319-654">Get the TLS alert value and level sent by the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-655">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-655">Prototype</span></span>

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a><span data-ttu-id="d8319-656">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-656">Description</span></span>

<span data-ttu-id="d8319-657">Ta usługa jest używana do pobierania poziomu alertu TLS i wartości, gdy host zdalny wysyła alert w odpowiedzi na jakiś problem lub błąd.</span><span class="sxs-lookup"><span data-stu-id="d8319-657">This service is used to retrieve the TLS alert level and value when the remote host sends an alert in response to some problem or error.</span></span>

<span data-ttu-id="d8319-658">Wartości parametrów alert_level i alert_value są prawidłowe tylko wtedy, gdy ta funkcja jest wywoływana natychmiast po wywołaniu interfejsu API TLS, który zwrócił stan NX_SECURE_TLS_ALERT_RECEIVED (0x114) wskazujący, że odebrano alert z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-658">The values of the alert_level and alert_value parameters are only valid if this function is called immediately following a TLS API call that returned a status of NX_SECURE_TLS_ALERT_RECEIVED (0x114) indicating that an alert was received from the remote host.</span></span>

<span data-ttu-id="d8319-659">Należy pamiętać, że jeśli protokół TLS hosta lokalnego wysyła alert, zwracane kody błędów są znacznie bardziej opisowe dla samego błędu niż alert protokołu TLS, ponieważ wartości alertów protokołu TLS zostały celowo pozostawione niejednoznaczne, aby zapobiec pewnym typom ataków (np. "uzupełnianie" lub "uzupełnienie").</span><span class="sxs-lookup"><span data-stu-id="d8319-659">Note that if the local host TLS sends an alert, the returned error codes are far more descriptive of the actual error than the TLS alert itself because TLS alert values are intentionally left ambiguous to prevent certain types of attack (such as a "padding oracle" attack or similar).</span></span>

<span data-ttu-id="d8319-660">Poziom alertu przyjmuje tylko jedną z dwóch wartości: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) lub NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span><span class="sxs-lookup"><span data-stu-id="d8319-660">The alert level only takes one of two values: NX_SECURE_TLS_ALERT_LEVEL_WARNING (0x1) or NX_SECURE_TLS_ALERT_LEVEL_FATAL (0x2).</span></span> <span data-ttu-id="d8319-661">Ogólnie rzecz biorąc, tylko alert CloseNotify (używany do wskazania pomyślne zakończenie sesji TLS) otrzyma poziom "ostrzeżenie", ale niektóre sytuacje związane z konfiguracją rozszerzeń mogą również być traktowane jako ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="d8319-661">In general, only the CloseNotify Alert (used to indicate a successful end to a TLS session) will be given a level of "Warning" though some extension configuration situations may also be considered warnings.</span></span> <span data-ttu-id="d8319-662">Większość alertów będzie "krytyczna" wskazujących potencjalny błąd zabezpieczeń i powodująca natychmiastowe zamknięcie połączenia TLS (uzgadnianie lub sesja).</span><span class="sxs-lookup"><span data-stu-id="d8319-662">The vast majority of alerts will be "Fatal" indicating a potential security failure and resulting in immediate closure of the TLS connection (handshake or session).</span></span>

<span data-ttu-id="d8319-663">Wartości alertów protokołu TLS są zdefiniowane w specyfikacjach RFC protokołu TLS. Oto listę z RFC 5246 (TLSv 1.2) dla celów informacyjnych:</span><span class="sxs-lookup"><span data-stu-id="d8319-663">The TLS alert values are defined in the TLS RFCs, here is the list from RFC 5246 (TLSv1.2) for reference:</span></span>

| <span data-ttu-id="d8319-664">Nazwa alertu</span><span class="sxs-lookup"><span data-stu-id="d8319-664">Alert Name</span></span>                     | <span data-ttu-id="d8319-665">Wartość</span><span class="sxs-lookup"><span data-stu-id="d8319-665">Value</span></span> | <span data-ttu-id="d8319-666">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-666">Description</span></span>                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="d8319-667">close_notify</span><span class="sxs-lookup"><span data-stu-id="d8319-667">close_notify</span></span>                  | <span data-ttu-id="d8319-668">0</span><span class="sxs-lookup"><span data-stu-id="d8319-668">0</span></span>     | <span data-ttu-id="d8319-669">Brak błędów, wskazuje pomyślne zakończenie sesji</span><span class="sxs-lookup"><span data-stu-id="d8319-669">No error, indicates successful session end</span></span>                                                                                                                   |
| <span data-ttu-id="d8319-670">unexpected_message</span><span class="sxs-lookup"><span data-stu-id="d8319-670">unexpected_message</span></span>            | <span data-ttu-id="d8319-671">10</span><span class="sxs-lookup"><span data-stu-id="d8319-671">10</span></span>    | <span data-ttu-id="d8319-672">Protokół TLS odebrał nieoczekiwany lub nieaktualny komunikat</span><span class="sxs-lookup"><span data-stu-id="d8319-672">TLS received an unexpected or out-of-order message</span></span>                                                                                                           |
| <span data-ttu-id="d8319-673">bad_record_mac</span><span class="sxs-lookup"><span data-stu-id="d8319-673">bad_record_mac</span></span>               | <span data-ttu-id="d8319-674">20</span><span class="sxs-lookup"><span data-stu-id="d8319-674">20</span></span>    | <span data-ttu-id="d8319-675">Nie można zweryfikować odszyfrowania i/lub komputera MAC</span><span class="sxs-lookup"><span data-stu-id="d8319-675">Decryption and/or MAC verification failed</span></span>                                                                                                                    |
| <span data-ttu-id="d8319-676">decryption_failed_RESERVED</span><span class="sxs-lookup"><span data-stu-id="d8319-676">decryption_failed_RESERVED</span></span>   | <span data-ttu-id="d8319-677">21</span><span class="sxs-lookup"><span data-stu-id="d8319-677">21</span></span>    | <span data-ttu-id="d8319-678">**Przestarzałe** Odszyfrowanie nie powiodło się (przestarzałe z powodu dopełnienia ataków Oracle)</span><span class="sxs-lookup"><span data-stu-id="d8319-678">**DEPRECATED** Decryption failed (deprecated due to padding oracle attacks)</span></span>                                                                                      |
| <span data-ttu-id="d8319-679">record_overflow</span><span class="sxs-lookup"><span data-stu-id="d8319-679">record_overflow</span></span>               | <span data-ttu-id="d8319-680">22</span><span class="sxs-lookup"><span data-stu-id="d8319-680">22</span></span>    | <span data-ttu-id="d8319-681">Odebrano rekord, który jest większy niż maksymalny rozmiar rekordu TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-681">A record was received that is larger than the TLS maximum record size</span></span>                                                                                        |
| <span data-ttu-id="d8319-682">decompression_failure</span><span class="sxs-lookup"><span data-stu-id="d8319-682">decompression_failure</span></span>         | <span data-ttu-id="d8319-683">30</span><span class="sxs-lookup"><span data-stu-id="d8319-683">30</span></span>    | <span data-ttu-id="d8319-684">Wystąpił problem podczas kompresji/dekompresji rekordu TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-684">A problem was encountered in compression/decompression of a TLS record</span></span>                                                                                       |
| <span data-ttu-id="d8319-685">handshake_failure</span><span class="sxs-lookup"><span data-stu-id="d8319-685">handshake_failure</span></span>             | <span data-ttu-id="d8319-686">40</span><span class="sxs-lookup"><span data-stu-id="d8319-686">40</span></span>    | <span data-ttu-id="d8319-687">Wystąpił nieokreślony błąd uzgadniania, który nie jest objęty innym alertem</span><span class="sxs-lookup"><span data-stu-id="d8319-687">Some unspecified handshake error occurred that isn't covered by a different alert</span></span>                                                                            |
| <span data-ttu-id="d8319-688">no_certificate_RESERVED</span><span class="sxs-lookup"><span data-stu-id="d8319-688">no_certificate_RESERVED</span></span>      | <span data-ttu-id="d8319-689">41</span><span class="sxs-lookup"><span data-stu-id="d8319-689">41</span></span>    | <span data-ttu-id="d8319-690">**Przestarzałe** w protokole TLS (tylko protokół SSL)</span><span class="sxs-lookup"><span data-stu-id="d8319-690">**DEPRECATED** in TLS (SSL only)</span></span>                                                                                                                                 |
| <span data-ttu-id="d8319-691">bad_certificate</span><span class="sxs-lookup"><span data-stu-id="d8319-691">bad_certificate</span></span>               | <span data-ttu-id="d8319-692">42</span><span class="sxs-lookup"><span data-stu-id="d8319-692">42</span></span>    | <span data-ttu-id="d8319-693">Otrzymany certyfikat zawiera nieprawidłowe formatowanie lub podpisy</span><span class="sxs-lookup"><span data-stu-id="d8319-693">A certificate that was received contained invalid formatting or signatures</span></span>                                                                                   |
| <span data-ttu-id="d8319-694">unsupported_certificate</span><span class="sxs-lookup"><span data-stu-id="d8319-694">unsupported_certificate</span></span>       | <span data-ttu-id="d8319-695">43</span><span class="sxs-lookup"><span data-stu-id="d8319-695">43</span></span>    | <span data-ttu-id="d8319-696">Odebrano certyfikat z nieprawidłowym typem (np. certyfikat tylko do podpisywania używany do uwierzytelniania serwera TLS)</span><span class="sxs-lookup"><span data-stu-id="d8319-696">A certificate was received that was of an invalid type (e.g. signing-only certificate used for TLS server authentication)</span></span>                                    |
| <span data-ttu-id="d8319-697">certificate_revoked</span><span class="sxs-lookup"><span data-stu-id="d8319-697">certificate_revoked</span></span>           | <span data-ttu-id="d8319-698">44</span><span class="sxs-lookup"><span data-stu-id="d8319-698">44</span></span>    | <span data-ttu-id="d8319-699">Stan certyfikatu (podany przez listę CRL lub OCSP) został wskazany jako "odwołany"</span><span class="sxs-lookup"><span data-stu-id="d8319-699">The certificate status (as provided by a CRL or OCSP) was indicated as being "revoked"</span></span>                                                                       |
| <span data-ttu-id="d8319-700">certificate_expired</span><span class="sxs-lookup"><span data-stu-id="d8319-700">certificate_expired</span></span>           | <span data-ttu-id="d8319-701">45</span><span class="sxs-lookup"><span data-stu-id="d8319-701">45</span></span>    | <span data-ttu-id="d8319-702">Otrzymany certyfikat był poza prawidłowym zakresem dat (nie jest jeszcze prawidłowy lub wygasł)</span><span class="sxs-lookup"><span data-stu-id="d8319-702">The received certificate was outside it's valid date range (either not valid yet or expired)</span></span>                                                                 |
| <span data-ttu-id="d8319-703">certificate_unknown</span><span class="sxs-lookup"><span data-stu-id="d8319-703">certificate_unknown</span></span>           | <span data-ttu-id="d8319-704">46</span><span class="sxs-lookup"><span data-stu-id="d8319-704">46</span></span>    | <span data-ttu-id="d8319-705">Napotkano nieznany problem z certyfikatem, który nie został objęty innymi alertami</span><span class="sxs-lookup"><span data-stu-id="d8319-705">Some unknown certificate issue was encountered that was not covered by other alerts</span></span>                                                                          |
| <span data-ttu-id="d8319-706">illegal_parameter</span><span class="sxs-lookup"><span data-stu-id="d8319-706">illegal_parameter</span></span>             | <span data-ttu-id="d8319-707">47</span><span class="sxs-lookup"><span data-stu-id="d8319-707">47</span></span>    | <span data-ttu-id="d8319-708">Niektóre konfiguracje lub negocjowane wartości w uzgadnianiu protokołu TLS były nieprawidłowe lub poza zakresem</span><span class="sxs-lookup"><span data-stu-id="d8319-708">Some configuration or negotiated value in the TLS handshake was invalid or out of range</span></span>                                                                      |
| <span data-ttu-id="d8319-709">unknown_ca</span><span class="sxs-lookup"><span data-stu-id="d8319-709">unknown_ca</span></span>                    | <span data-ttu-id="d8319-710">48</span><span class="sxs-lookup"><span data-stu-id="d8319-710">48</span></span>    | <span data-ttu-id="d8319-711">Nie można śledzić otrzymanego certyfikatu tożsamości za pośrednictwem łańcucha certyfikatów do certyfikatu zaufanego głównego urzędu certyfikacji.</span><span class="sxs-lookup"><span data-stu-id="d8319-711">The received identity certificate could not be traced via a certificate chain to a trusted root CA certificate.</span></span>                                              |
| <span data-ttu-id="d8319-712">access_denied</span><span class="sxs-lookup"><span data-stu-id="d8319-712">access_denied</span></span>                 | <span data-ttu-id="d8319-713">49</span><span class="sxs-lookup"><span data-stu-id="d8319-713">49</span></span>    | <span data-ttu-id="d8319-714">Wskazuje, że odebrano prawidłowy certyfikat, ale kontrola dostępu do aplikacji wskazywała, że certyfikat był nieprawidłowy dla żądanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="d8319-714">Indicates a valid certificate was received but application access control indicated that the certificate was invalid for the requested resources.</span></span>            |
| <span data-ttu-id="d8319-715">decode_error</span><span class="sxs-lookup"><span data-stu-id="d8319-715">decode_error</span></span>                  | <span data-ttu-id="d8319-716">50</span><span class="sxs-lookup"><span data-stu-id="d8319-716">50</span></span>    | <span data-ttu-id="d8319-717">Niektóre pola lub wartości w nagłówku TLS lub komunikacie uzgadniania są poza zakresem lub nieprawidłowe, co prowadzi do błędu podczas dekodowania rekordu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-717">Some field or value in a TLS header or handshake message was out of range or invalid, leading to a failure in decoding of a TLS record.</span></span>                      |
| <span data-ttu-id="d8319-718">decrypt_error</span><span class="sxs-lookup"><span data-stu-id="d8319-718">decrypt_error</span></span>                 | <span data-ttu-id="d8319-719">51</span><span class="sxs-lookup"><span data-stu-id="d8319-719">51</span></span>    | <span data-ttu-id="d8319-720">Nie można zweryfikować skrótu do sygnatury lub zakończonego komunikatu podczas uzgadniania protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-720">A signature or Finished message hash during the TLS handshake could not be verified.</span></span>                                                                         |
| <span data-ttu-id="d8319-721">export_restriction_RESERVED</span><span class="sxs-lookup"><span data-stu-id="d8319-721">export_restriction_RESERVED</span></span>  | <span data-ttu-id="d8319-722">60</span><span class="sxs-lookup"><span data-stu-id="d8319-722">60</span></span>    | <span data-ttu-id="d8319-723">PRZESTARZAŁe w TLSv 1.2</span><span class="sxs-lookup"><span data-stu-id="d8319-723">DEPRECATED in TLSv1.2</span></span>                                                                                                                                        |
| <span data-ttu-id="d8319-724">protocol_version</span><span class="sxs-lookup"><span data-stu-id="d8319-724">protocol_version</span></span>              | <span data-ttu-id="d8319-725">70</span><span class="sxs-lookup"><span data-stu-id="d8319-725">70</span></span>    | <span data-ttu-id="d8319-726">Wersja protokołu TLS negocjowana podczas uzgadniania jest rozpoznawana, ale nie jest obsługiwana (np. TLSv 1.0 została przedstawiona, ale nie została włączona).</span><span class="sxs-lookup"><span data-stu-id="d8319-726">The TLS protocol version negotiated during the handshake is recognized but not supported (e.g. TLSv1.0 was presented but not enabled).</span></span>                       |
| <span data-ttu-id="d8319-727">insufficient_security</span><span class="sxs-lookup"><span data-stu-id="d8319-727">insufficient_security</span></span>         | <span data-ttu-id="d8319-728">71</span><span class="sxs-lookup"><span data-stu-id="d8319-728">71</span></span>    | <span data-ttu-id="d8319-729">Wysyłany za każdym razem, gdy uzgadnianie nie powiedzie się z powodu braku bezpiecznych szyfrów (np. rozmiar klucza jest zbyt mały dla wymagań aplikacji)</span><span class="sxs-lookup"><span data-stu-id="d8319-729">Sent whenever a handshake fails due to a lack of secure ciphers (e.g. key size is too small for the application requirements)</span></span>                                |
| <span data-ttu-id="d8319-730">internal_error</span><span class="sxs-lookup"><span data-stu-id="d8319-730">internal_error</span></span>                | <span data-ttu-id="d8319-731">80</span><span class="sxs-lookup"><span data-stu-id="d8319-731">80</span></span>    | <span data-ttu-id="d8319-732">Wystąpił błąd niezwiązany z protokołem TLS (np. problemy z alokacją pamięci, problemy z aplikacją), co spowodowało przerwaną sesję protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-732">Some non-TLS error (e.g. memory allocation problems, application issues) occurred resulting in a broken TLS session.</span></span>                                         |
| <span data-ttu-id="d8319-733">user_canceled</span><span class="sxs-lookup"><span data-stu-id="d8319-733">user_canceled</span></span>                 | <span data-ttu-id="d8319-734">90</span><span class="sxs-lookup"><span data-stu-id="d8319-734">90</span></span>    | <span data-ttu-id="d8319-735">Zwracany, jeśli sesja TLS została anulowana przez użytkownika lub aplikację przed ukończeniem uzgadniania (podobnego do CloseNotify).</span><span class="sxs-lookup"><span data-stu-id="d8319-735">Returned if the TLS session is cancelled by a user or application before the handshake is complete (similar to CloseNotify).</span></span>                                 |
| <span data-ttu-id="d8319-736">no_renegotiation</span><span class="sxs-lookup"><span data-stu-id="d8319-736">no_renegotiation</span></span>              | <span data-ttu-id="d8319-737">100</span><span class="sxs-lookup"><span data-stu-id="d8319-737">100</span></span>   | <span data-ttu-id="d8319-738">Indiates, że host zdalny nie chce wykonać uzgadniania renegocjacji protokołu TLS w odpowiedzi na żądanie ponownego negocjowania.</span><span class="sxs-lookup"><span data-stu-id="d8319-738">Indiates that the remote host is not willing to perform TLS renegotiation handshakes in response to a renegotiation request.</span></span>                                 |
| <span data-ttu-id="d8319-739">unsupported_extension</span><span class="sxs-lookup"><span data-stu-id="d8319-739">unsupported_extension</span></span>         | <span data-ttu-id="d8319-740">110</span><span class="sxs-lookup"><span data-stu-id="d8319-740">110</span></span>   | <span data-ttu-id="d8319-741">Wysyłany, gdy klient TLS odbiera ServerHello z rozszerzeniami, które nie są jawnie zadawane w początkowej komunikacie ClientHello (wskazuje na to, że wystąpił problem z serwerem).</span><span class="sxs-lookup"><span data-stu-id="d8319-741">Sent if a TLS Client receives a ServerHello containing extensions not explicitly asked for in the initial ClientHello (indicating the server has a problem).</span></span> |

### <a name="parameters"></a><span data-ttu-id="d8319-742">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-742">Parameters</span></span>

- <span data-ttu-id="d8319-743">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-743">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="d8319-744">**alert_level** Zwróć poziom odebranego alertu (ostrzeżenie lub krytyczny).</span><span class="sxs-lookup"><span data-stu-id="d8319-744">**alert_level** Return the level of the received alert (warning or fatal).</span></span>
- <span data-ttu-id="d8319-745">**alert_value** Zwraca wartość otrzymanego alertu (patrz tabela).</span><span class="sxs-lookup"><span data-stu-id="d8319-745">**alert_value** Return the value of the received alert (see table).</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-746">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-746">Return Values</span></span>

- <span data-ttu-id="d8319-747">Operacja powiodła się **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="d8319-747">**NX_SUCCESS** (0x00) Successful operation.</span></span>
- <span data-ttu-id="d8319-748">**NX_PTR_ERROR** (0X07) Nieprawidłowa sesja TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-748">**NX_PTR_ERROR** (0x07) Invalid TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-749">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-749">Allowed From</span></span>

<span data-ttu-id="d8319-750">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-750">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-751">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-751">Example</span></span>

```C
/* Return values. */
UINT status, alert_level, alert_value;


/* Start a TLS session.  */
status =  nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Check for “alert received” error. */
if(status == NX_SECURE_TLS_ALERT_RECEIVED)
{

        /* Get the alert level and value. */
        status =  nx_secure_tls_session_alert_value_get(&tls_session,
                                             &alert_level, &alert_value);

        /* Print out the received alert level and value. */
        printf("Alert recieved. Value: %d, Level: %d\n", alert_value,
                alert_level);
}
else if(status != NX_SUCCESS)
{
    /* Additional error handling. */
}
```

### <a name="see-also"></a><span data-ttu-id="d8319-752">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-752">See Also</span></span>

- <span data-ttu-id="d8319-753">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-753">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-754">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="d8319-754">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="d8319-755">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-755">nx_secure_tls_session_receive</span></span>

## <a name="nx_secure_tls_session_certificate_callback_set"></a><span data-ttu-id="d8319-756">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-756">nx_secure_tls_session_certificate_callback_set</span></span>

<span data-ttu-id="d8319-757">Konfigurowanie wywołania zwrotnego protokołu TLS do użycia na potrzeby dodatkowej weryfikacji certyfikatu</span><span class="sxs-lookup"><span data-stu-id="d8319-757">Set up a callback for TLS to use for additional certificate validation</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-758">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-758">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a><span data-ttu-id="d8319-759">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-759">Description</span></span>

<span data-ttu-id="d8319-760">Ta usługa przypisuje wskaźnik funkcji do sesji protokołu TLS, która będzie wywoływała protokół TLS w przypadku odebrania certyfikatu z hosta zdalnego, co umożliwia aplikacji wykonywanie testów weryfikacji, takich jak Walidacja DNS, Odwoływanie certyfikatów i wymuszanie zasad certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d8319-760">This service assigns a function pointer to a TLS session that TLS will invoke when a certificate is received from a remote host, allowing the application to perform validation checks such as DNS validation, certificate revocation, and certificate policy enforcement.</span></span>

<span data-ttu-id="d8319-761">NetX Secure TLS będzie przeprowadzać podstawowe sprawdzanie poprawności ścieżki X. 509 na certyfikacie przed wywołaniem wywołania zwrotnego w celu zapewnienia, że certyfikat może być śledzony do certyfikatu w magazynie zaufanych certyfikatów TLS, ale wszystkie inne walidacje będą obsługiwane przez to wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="d8319-761">NetX Secure TLS will perform basic X.509 path validation on the certificate before invoking the callback to assure that the certificate can be traced to a certificate in the TLS trusted certificate store, but all other validation will be handled by this callback.</span></span>

<span data-ttu-id="d8319-762">Wywołanie zwrotne udostępnia wskaźnik sesji TLS i wskaźnik do certyfikatu tożsamości hosta zdalnego (liścia w łańcuchu certyfikatów).</span><span class="sxs-lookup"><span data-stu-id="d8319-762">The callback provides the TLS session pointer and a pointer to the remote host identity certificate (the leaf in the certificate chain).</span></span> <span data-ttu-id="d8319-763">Wywołanie zwrotne powinno zwracać NX_SUCCESS, jeśli sprawdzanie poprawności zakończy się powodzeniem, w przeciwnym razie powinna zwrócić kod błędu wskazujący błąd walidacji.</span><span class="sxs-lookup"><span data-stu-id="d8319-763">The callback should return NX_SUCCESS if all validation is successful, otherwise it should return an error code indicating the validation failure.</span></span> <span data-ttu-id="d8319-764">Każda wartość inna niż NX_SUCCESS spowoduje natychmiastowe przerwanie uzgadniania protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-764">Any value other than NX_SUCCESS will cause the TLS handshake to immediately abort.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-765">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-765">Parameters</span></span>

- <span data-ttu-id="d8319-766">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-766">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="d8319-767">**func_ptr** Wskaźnik do funkcji wywołania zwrotnego walidacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-767">**func_ptr** Pointer to the certificate validation callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-768">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-768">Return Values</span></span>

- <span data-ttu-id="d8319-769">**NX_SUCCESS** (0X00) pomyślne alokacja wskaźnika funkcji.</span><span class="sxs-lookup"><span data-stu-id="d8319-769">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="d8319-770">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-770">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-771">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-771">Allowed From</span></span>

<span data-ttu-id="d8319-772">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-772">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-773">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-773">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
    /* Certificate validation checking goes here. */
    return(NX_SUCCESS);
}

/* In TLS setup routine. */
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                            certificate_callback);

        /* If status is NX_SUCCESS the certificate callback was added.  */
}
```

### <a name="see-also"></a><span data-ttu-id="d8319-774">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-774">See Also</span></span>

- <span data-ttu-id="d8319-775">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-775">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-776">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="d8319-776">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="d8319-777">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="d8319-777">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_tls_session_client_callback_set"></a><span data-ttu-id="d8319-778">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-778">nx_secure_tls_session_client_callback_set</span></span>

<span data-ttu-id="d8319-779">Konfigurowanie wywołania zwrotnego protokołu TLS do wywołania na początku uzgadniania klienta TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-779">Set up a callback for TLS to invoke at the beginning of a TLS Client handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-780">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-780">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="d8319-781">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-781">Description</span></span>

<span data-ttu-id="d8319-782">Ta usługa przypisuje wskaźnik funkcji do sesji TLS, która będzie wywoływała protokół TLS, gdy uzgadnianie klienta TLS odebrało komunikat ServerHelloDone.</span><span class="sxs-lookup"><span data-stu-id="d8319-782">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Client handshake has received a ServerHelloDone message.</span></span> <span data-ttu-id="d8319-783">Funkcja wywołania zwrotnego umożliwia aplikacji przetwarzanie wszelkich rozszerzeń TLS z odebranego komunikatu ServerHello, który wymaga wprowadzenia danych lub podejmowania decyzji.</span><span class="sxs-lookup"><span data-stu-id="d8319-783">The callback function allows an application to process any TLS extensions from the received ServerHello message that require input or decision making.</span></span>

<span data-ttu-id="d8319-784">Wywołanie zwrotne jest wykonywane z wywoływaniem bloku sterowania sesją TLS i tablicą obiektów NX_SECURE_TLS_HELLO_EXTENSION.</span><span class="sxs-lookup"><span data-stu-id="d8319-784">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="d8319-785">Tablica obiektów rozszerzeń jest przeznaczona do przekazywania do funkcji pomocnika, która będzie znajdować i analizować określone rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="d8319-785">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="d8319-786">Obecnie nie ma określonych rozszerzeń, które są obsługiwane w NetX Secure, które wymagają danych wejściowych klienta TLS, ale wywołanie zwrotne jest dostępne dla projektantów aplikacji obsługujących niestandardowe lub nowe rozszerzenia, które mogą stać się dostępne.</span><span class="sxs-lookup"><span data-stu-id="d8319-786">Currently, there are no specific extensions supported in NetX Secure that require TLS Client input, but the callback is available for application designers to handle custom or new extensions that may become available.</span></span> <span data-ttu-id="d8319-787">Przykładowa funkcja pomocnicza, która analizuje rozszerzenia protokołu TLS podane w komunikatach Hello, znajduje się w temacie *nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="d8319-787">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="d8319-788">Wywołania zwrotnego klienta można również użyć do wybrania aktywnego certyfikatu tożsamości przy użyciu *nx_secure_tls_active_certificate_set* dla klienta protokołu TLS w przypadku, gdy serwer zdalny zażądał certyfikatu i podano informacje umożliwiające klientowi protokołu TLS wybranie określonego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-788">The client callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Client in the event that the remote server has requested a certificate and provided information to allow the TLS Client to select a specific certificate.</span></span> <span data-ttu-id="d8319-789">Aby uzyskać więcej informacji, zobacz informacje o nx_secure_tls_active_certificate_set.</span><span class="sxs-lookup"><span data-stu-id="d8319-789">See the reference for nx_secure_tls_active_certificate_set for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-790">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-790">Parameters</span></span>

- <span data-ttu-id="d8319-791">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-791">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="d8319-792">**func_ptr** Wskaźnik do funkcji wywołania zwrotnego klienta TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-792">**func_ptr** Pointer to the TLS Client callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-793">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-793">Return Values</span></span>

- <span data-ttu-id="d8319-794">**NX_SUCCESS** (0X00) pomyślne alokacja wskaźnika funkcji.</span><span class="sxs-lookup"><span data-stu-id="d8319-794">**NX_SUCCESS** (0x00) Successful allocation of function pointer.</span></span>
- <span data-ttu-id="d8319-795">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-795">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-796">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-796">Allowed From</span></span>

<span data-ttu-id="d8319-797">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-797">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-798">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-798">Example</span></span>

```C
/* Callback routine used to process ServerHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the server). */

ULONG tls_client_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{

    /* Extension parsing would go here. */

    /* Set an active identity certificate – the certificate should have been added
       to the local store at application start with
       nx_secure_tls_local_certificate_add. */
    nx_secure_tls_active_certificate_set(session, &global_identity_certificate);

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
    /* Add callback to TLS session.  */
    status =  nx_secure_tls_session_client_callback_set(tls_session,
                                                        client_callback);

    /* If status is NX_SUCCESS the callback was added and will be invoked once
       a ServerHelloDone message is received. */

    return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="d8319-799">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-799">See Also</span></span>

- <span data-ttu-id="d8319-800">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-800">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-801">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-801">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="d8319-802">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="d8319-802">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a><span data-ttu-id="d8319-803">nx_secure_tls_session_x509_client_verify_configure</span><span class="sxs-lookup"><span data-stu-id="d8319-803">nx_secure_tls_session_x509_client_verify_configure</span></span>

<span data-ttu-id="d8319-804">Włącz weryfikację klienta X. 509 i Przydziel miejsce dla certyfikatów klienta</span><span class="sxs-lookup"><span data-stu-id="d8319-804">Enable client X.509 verification and allocate space for client certificates</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-805">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-805">Prototype</span></span>

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="d8319-806">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-806">Description</span></span>

<span data-ttu-id="d8319-807">Ta usługa umożliwia opcjonalne uwierzytelnianie klienta X. 509 dla wystąpienia serwera TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-807">This service enables the optional X.509 Client Authentication for a TLS Server instance.</span></span> <span data-ttu-id="d8319-808">Przydziela również miejsce niezbędne do przetwarzania łańcuchów certyfikatów przychodzących z hosta klienta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-808">It also allocates the space needed to process incoming certificate chains from the remote client host.</span></span> <span data-ttu-id="d8319-809">Certyfikaty dostarczone przez klienta zdalnego zostaną zweryfikowane względem zaufanych certyfikatów wystąpienia serwera TLS przypisane do usługi *nx_secure_tls_trusted_certificate_add.*</span><span class="sxs-lookup"><span data-stu-id="d8319-809">The certificates supplied by the remote client will be verified against the TLS server instance's trusted certificates, assigned with the service *nx_secure_tls_trusted_certificate_add.*</span></span>

<span data-ttu-id="d8319-810">W przypadku trybu klienta protokołu TLS wymagane jest przydzielenie certyfikatu zdalnego, a w zamian należy użyć *nx_secure_tls_remote_certificate_buffer_allocate* usługi.</span><span class="sxs-lookup"><span data-stu-id="d8319-810">For TLS Client mode, remote certificate allocation is required and the service *nx_secure_tls_remote_certificate_buffer_allocate* should be used instead.</span></span> <span data-ttu-id="d8319-811">Włączenie uwierzytelniania klienta X. 509 w wystąpieniu klienta TLS nie będzie miało żadnego efektu.</span><span class="sxs-lookup"><span data-stu-id="d8319-811">Enabling X.509 Client Authentication on a TLS Client instance will have no effect.</span></span>

<span data-ttu-id="d8319-812">Parametr *certificate_buffer* wskazuje miejsce przydzielenia do przechowywania przychodzących certyfikatów zdalnych i bloków sterowania wymaganych przez te certyfikaty.</span><span class="sxs-lookup"><span data-stu-id="d8319-812">The *certificate_buffer* parameter points to space allocated to store the incoming remote certificates and the control blocks needed for those certificates.</span></span> <span data-ttu-id="d8319-813">Bufor zostanie podzielony przez liczbę certyfikatów (*certs_number*) o równej części danego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-813">The buffer will be divided by the number of certificates (*certs_number*) with an equal portion given to each certificate.</span></span> <span data-ttu-id="d8319-814">Parametr *buffer_size* wskazuje rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="d8319-814">The *buffer_size* parameter indicates the size of the buffer.</span></span> <span data-ttu-id="d8319-815">Wymaganą ilość miejsca można znaleźć za pomocą następującej formuły:</span><span class="sxs-lookup"><span data-stu-id="d8319-815">The space needed can be found with the following formula:</span></span>

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

<span data-ttu-id="d8319-816">Typowe certyfikaty z kluczami RSA 2048 bitów przy użyciu algorytmu SHA-256 są w zakresie od 1000-2000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="d8319-816">Typical certificates with RSA keys of 2048 bits using SHA-256 for signatures are in the range of 1000-2000 bytes.</span></span> <span data-ttu-id="d8319-817">Bufor powinien być wystarczająco duży, aby zmniejszyć rozmiar każdego certyfikatu, ale w zależności od tego, czy certyfikaty hosta zdalnego mogą być znacznie mniejsze lub większe.</span><span class="sxs-lookup"><span data-stu-id="d8319-817">The buffer should be large enough to at least hold that size for each certificate, but depending on the remote host certificates may be significantly smaller or larger.</span></span> <span data-ttu-id="d8319-818">Należy pamiętać, że jeśli bufor jest za mały, aby pomieścić certyfikat przychodzący, uzgadnianie TLS zakończy się błędem.</span><span class="sxs-lookup"><span data-stu-id="d8319-818">Note that if the buffer is too small to hold the incoming certificate, the TLS handshake will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-819">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-819">Parameters</span></span>

- <span data-ttu-id="d8319-820">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-820">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="d8319-821">**certs_number** Liczba certyfikatów do przydzielenia z podanego buforu.</span><span class="sxs-lookup"><span data-stu-id="d8319-821">**certs_number** Number of certificates to allocate from the provided buffer.</span></span>
- <span data-ttu-id="d8319-822">**certificate_buffer** Wskaźnik do buforu w celu przechowywania certyfikatów odebranych z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-822">**certificate_buffer** Pointer to a buffer to hold certificates received from a remote host.</span></span>
- <span data-ttu-id="d8319-823">**buffer_size** Rozmiar buforu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-823">**buffer_size** Size of the certificate buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-824">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-824">Return Values</span></span>

- <span data-ttu-id="d8319-825">**NX_SUCCESS** (0X00) pomyślne przypisanie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-825">**NX_SUCCESS** (0x00)Successful allocation of certificate.</span></span>
- <span data-ttu-id="d8319-826">**NX_PTR_ERROR** (0X07) Nieprawidłowa sesja protokołu TLS lub wskaźnik buforu.</span><span class="sxs-lookup"><span data-stu-id="d8319-826">**NX_PTR_ERROR** (0x07) Invalid TLS session or buffer pointer.</span></span>
- <span data-ttu-id="d8319-827">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) dostarczony bufor jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="d8319-827">**NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** (0x12D) The supplied buffer was too small.</span></span>
- <span data-ttu-id="d8319-828">**NX_INVALID_PARAMETERS** (0x4D) bufor był zbyt mały, aby pomieścić żądaną liczbę certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d8319-828">**NX_INVALID_PARAMETERS** (0x4D) The buffer was too small to hold the desired number of certificates.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-829">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-829">Allowed From</span></span>

<span data-ttu-id="d8319-830">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-830">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-831">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-831">Example</span></span>

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE          (CERTIFICATE_NUMBER * \
                                (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Enable X.509 Client verification and allocate certificate space in our TLS
   Server session.  */
status =  nx_secure_tls_session_x509_client_verify_configure(&tls_session,
                                                    CERTIFICATE_NUMBER,
                                                    certificate_buffer,
                                                    BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-832">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-832">See Also</span></span>

- <span data-ttu-id="d8319-833">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-833">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-834">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-834">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-835">nx_secure_tls_remote_certificate_buffer_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-835">nx_secure_tls_remote_certificate_buffer_allocate</span></span>

## <a name="nx_secure_tls_session_client_verify_disable"></a><span data-ttu-id="d8319-836">nx_secure_tls_session_client_verify_disable</span><span class="sxs-lookup"><span data-stu-id="d8319-836">nx_secure_tls_session_client_verify_disable</span></span>

<span data-ttu-id="d8319-837">Wyłączanie uwierzytelniania certyfikatu klienta dla sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-837">Disable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-838">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-838">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="d8319-839">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-839">Description</span></span>

<span data-ttu-id="d8319-840">Ta usługa wyłącza uwierzytelnianie certyfikatu klienta dla określonej sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-840">This service disables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="d8319-841">Aby uzyskać więcej informacji, zobacz nx_secure_tls_session_client_verify_enable.</span><span class="sxs-lookup"><span data-stu-id="d8319-841">See nx_secure_tls_session_client_verify_enable for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-842">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-842">Parameters</span></span>

- <span data-ttu-id="d8319-843">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-843">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-844">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-844">Return Values</span></span>

- <span data-ttu-id="d8319-845">Pomyślna zmiana stanu **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="d8319-845">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="d8319-846">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-846">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-847">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-847">Allowed From</span></span>

<span data-ttu-id="d8319-848">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-848">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-849">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-849">Example</span></span>

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-850">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-850">See Also</span></span>

- <span data-ttu-id="d8319-851">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="d8319-851">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="d8319-852">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-852">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-853">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-853">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_client_verify_enable"></a><span data-ttu-id="d8319-854">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="d8319-854">nx_secure_tls_session_client_verify_enable</span></span>

<span data-ttu-id="d8319-855">Włącz uwierzytelnianie certyfikatu klienta dla sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-855">Enable Client Certificate Authentication for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-856">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-856">Prototype</span></span>

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="d8319-857">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-857">Description</span></span>

<span data-ttu-id="d8319-858">Ta usługa umożliwia uwierzytelnianie certyfikatu klienta dla określonej sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-858">This service enables Client Certificate Authentication for a specific TLS session.</span></span> <span data-ttu-id="d8319-859">Włączenie uwierzytelniania certyfikatu klienta dla wystąpienia serwera TLS spowoduje, że serwer TLS zażąda certyfikatu od dowolnego klienta zdalnego protokołu TLS podczas początkowego uzgadniania protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-859">Enabling Client Certificate Authentication for a TLS Server instance will cause the TLS Server to request a certificate from any remote TLS Client during the initial TLS handshake.</span></span> <span data-ttu-id="d8319-860">Certyfikat otrzymany od zdalnego klienta protokołu TLS jest dołączany przez komunikat CertificateVerify, którego serwer TLS używa do sprawdzenia, czy klient jest właścicielem certyfikatu (ma dostęp do klucza prywatnego skojarzonego z tym certyfikatem).</span><span class="sxs-lookup"><span data-stu-id="d8319-860">The certificate received from the remote TLS Client is accompanied by a CertificateVerify message, which the TLS Server uses to verify that the Client owns the certificate (has access to the private key associated with that certificate).</span></span>

<span data-ttu-id="d8319-861">Jeśli podany certyfikat może zostać zweryfikowany i wyśledzony z powrotem do certyfikatu w zaufanym magazynie certyfikatów serwera TLS za pośrednictwem łańcucha certyfikatów X. 509, zdalny klient protokołu TLS jest uwierzytelniany, a uzgadnianie jest przeprowadzane.</span><span class="sxs-lookup"><span data-stu-id="d8319-861">If the provided certificate can be verified and traced back to a certificate in the TLS Server trusted certificate store via an X.509 certificate chain, the remote TLS Client is authenticated and the handshake proceeds.</span></span> <span data-ttu-id="d8319-862">W przypadku wystąpienia błędów podczas przetwarzania certyfikatu lub komunikatu CertificateVerify, uzgadnianie TLS zostanie zakończone z błędem.</span><span class="sxs-lookup"><span data-stu-id="d8319-862">In case of any errors in processing the certificate or CertificateVerify message, the TLS handshake ends with an error.</span></span>

> [!NOTE]
> <span data-ttu-id="d8319-863">*Serwer TLS musi mieć co najmniej jeden certyfikat w zaufanym magazynie, który został dodany do nx_secure_tls_trusted_certificate_add lub uwierzytelnianie będzie zawsze kończyć się niepowodzeniem.*</span><span class="sxs-lookup"><span data-stu-id="d8319-863">*The TLS Server must have at least one certificate in its trusted store added with nx_secure_tls_trusted_certificate_add or authentication will always fail.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-864">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-864">Parameters</span></span>

- <span data-ttu-id="d8319-865">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-865">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-866">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-866">Return Values</span></span>

- <span data-ttu-id="d8319-867">Pomyślna zmiana stanu **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="d8319-867">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="d8319-868">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-868">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-869">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-869">Allowed From</span></span>

<span data-ttu-id="d8319-870">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-871">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-871">Example</span></span>

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-872">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-872">See Also</span></span>

- <span data-ttu-id="d8319-873">nx_secure_tls_session_client_verify_enable</span><span class="sxs-lookup"><span data-stu-id="d8319-873">nx_secure_tls_session_client_verify_enable</span></span>
- <span data-ttu-id="d8319-874">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-874">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-875">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-875">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-876">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-876">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_tls_session_create"></a><span data-ttu-id="d8319-877">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-877">nx_secure_tls_session_create</span></span>

<span data-ttu-id="d8319-878">Tworzenie bezpiecznej sesji protokołu TLS NetX na potrzeby bezpiecznej komunikacji</span><span class="sxs-lookup"><span data-stu-id="d8319-878">Create a NetX Secure TLS Session for secure communications</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-879">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-879">Prototype</span></span>

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a><span data-ttu-id="d8319-880">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-880">Description</span></span>

<span data-ttu-id="d8319-881">Ta usługa inicjuje NX_SECURE_TLS_SESSION wystąpienia struktury do użycia podczas ustanawiania bezpiecznej komunikacji TLS za pośrednictwem połączenia sieciowego.</span><span class="sxs-lookup"><span data-stu-id="d8319-881">This service initializes an NX_SECURE_TLS_SESSION structure instance for use in establishing secure TLS communications over a network connection.</span></span>

<span data-ttu-id="d8319-882">Metoda przyjmuje NX_SECURE_TLS_CRYPTO obiektu, który jest wypełniony metodami kryptograficznymi, które mają być używane na potrzeby protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-882">The method takes a NX_SECURE_TLS_CRYPTO object that is populated with the available cryptographic methods to be used for TLS.</span></span> <span data-ttu-id="d8319-883">*Encryption_metadata_area* wskazuje bufor przydzielony do użycia przez protokół TLS dla "metadanych" używanych przez metody kryptograficzne w tabeli NX_SECURE_TLS_CRYPTO dla obliczeń.</span><span class="sxs-lookup"><span data-stu-id="d8319-883">The *encryption_metadata_area* points to a buffer allocated for use by TLS for the "metadata" used by the cryptographic methods in the NX_SECURE_TLS_CRYPTO table for calculations.</span></span> <span data-ttu-id="d8319-884">Rozmiar tabeli można określić za pomocą usługi nx_secure_tls_metadata_size_calculate.</span><span class="sxs-lookup"><span data-stu-id="d8319-884">The size of the table can be determined by using the nx_secure_tls_metadata_size_calculate service.</span></span> <span data-ttu-id="d8319-885">Zobacz sekcję "Kryptografia w NetX Secure TLS" w rozdziale 3, aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="d8319-885">See the section "Cryptography in NetX Secure TLS" in Chapter 3 for more details.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-886">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-886">Parameters</span></span>

- <span data-ttu-id="d8319-887">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-887">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="d8319-888">**cipher_table** Wskaźnik do metod kryptograficznych protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-888">**cipher_table** Pointer to TLS cryptographic methods.</span></span>
- <span data-ttu-id="d8319-889">**encryption_metadata_area** Wskaźnik na miejsce dla metadanych kryptografii.</span><span class="sxs-lookup"><span data-stu-id="d8319-889">**encryption_metadata_area** Pointer to space for cryptography metadata.</span></span>
- <span data-ttu-id="d8319-890">**encryption_metadata_size** Rozmiar buforu metadanych.</span><span class="sxs-lookup"><span data-stu-id="d8319-890">**encryption_metadata_size** Size of the metadata buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-891">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-891">Return Values</span></span>

- <span data-ttu-id="d8319-892">**NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-892">**NX_SUCCESS** (0x00)Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="d8319-893">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d8319-893">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="d8319-894">**NX_INVALID_PARAMETERS** (0x4D) bufor metadanych był za mały dla określonych metod.</span><span class="sxs-lookup"><span data-stu-id="d8319-894">**NX_INVALID_PARAMETERS** (0x4D) The metadata buffer was too small for the given methods.</span></span>
- <span data-ttu-id="d8319-895">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) wymagana Metoda szyfrowania dla włączonej wersji protokołu TLS nie została podana w tabeli szyfru.</span><span class="sxs-lookup"><span data-stu-id="d8319-895">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A required cipher method for the enabled version of TLS was not supplied in the cipher table.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-896">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-896">Allowed From</span></span>

<span data-ttu-id="d8319-897">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-897">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-898">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-898">Example</span></span>

```C
/* Reference the platform-specific TLS cryptographic method table. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Declare a buffer for the cryptographic metadata. The size should be calculated
   using nx_secure_tls_metadata_size_calculate. */
UCHAR crypto_metadata[4500];

/* Initialize TLS session.  */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* If status is NX_SUCCESS the TLS Session was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-899">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-899">See Also</span></span>

- <span data-ttu-id="d8319-900">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-900">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-901">nx_secure_tls_metadata_size_calculate</span><span class="sxs-lookup"><span data-stu-id="d8319-901">nx_secure_tls_metadata_size_calculate</span></span>
- <span data-ttu-id="d8319-902">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-902">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-903">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-903">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-904">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="d8319-904">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="d8319-905">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="d8319-905">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="d8319-906">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-906">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="d8319-907">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="d8319-907">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="d8319-908">Kryptografia w NetX Secure TLS w rozdziale 3</span><span class="sxs-lookup"><span data-stu-id="d8319-908">Cryptography in NetX Secure TLS in Chapter 3</span></span>

## <a name="nx_secure_tls_session_delete"></a><span data-ttu-id="d8319-909">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="d8319-909">nx_secure_tls_session_delete</span></span>

<span data-ttu-id="d8319-910">Usuwanie sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-910">Delete a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-911">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-911">Prototype</span></span>

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="d8319-912">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-912">Description</span></span>

<span data-ttu-id="d8319-913">Ta usługa usuwa sesję TLS reprezentowaną przez wystąpienie struktury NX_SECURE_TLS_SESSION i zwalnia wszystkie zasoby systemowe należące do tego wystąpienia sesji.</span><span class="sxs-lookup"><span data-stu-id="d8319-913">This service deletes a TLS session represented by an NX_SECURE_TLS_SESSION structure instance and releases all system resources owned by that session instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-914">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-914">Parameters</span></span>

- <span data-ttu-id="d8319-915">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-915">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-916">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-916">Return Values</span></span>

- <span data-ttu-id="d8319-917">**NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-917">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="d8319-918">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d8319-918">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-919">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-919">Allowed From</span></span>

<span data-ttu-id="d8319-920">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-920">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-921">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-921">Example</span></span>

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-922">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-922">See Also</span></span>

- <span data-ttu-id="d8319-923">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-923">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-924">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-924">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-925">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-925">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-926">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="d8319-926">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="d8319-927">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="d8319-927">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="d8319-928">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-928">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="d8319-929">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-929">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_end"></a><span data-ttu-id="d8319-930">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="d8319-930">nx_secure_tls_session_end</span></span>

<span data-ttu-id="d8319-931">Kończenie aktywnej sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-931">End an active NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-932">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-932">Prototype</span></span>

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d8319-933">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-933">Description</span></span>

<span data-ttu-id="d8319-934">Ta usługa służy do kończenia sesji TLS reprezentowanej przez wystąpienie struktury NX_SECURE_TLS_SESSION przez wysłanie komunikatu CloseNotify TLS do hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-934">This service ends a TLS session represented by an NX_SECURE_TLS_SESSION structure instance by sending the TLS CloseNotify message to the remote host.</span></span> <span data-ttu-id="d8319-935">Następnie usługa czeka na odpowiedź hosta zdalnego przy użyciu własnego komunikatu CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="d8319-935">The service then waits for the remote host to respond with its own CloseNotify message.</span></span>

<span data-ttu-id="d8319-936">Jeśli host zdalny nie wyśle komunikatu CloseNotify, protokół TLS uważa ten błąd i możliwe naruszenie zabezpieczeń, dlatego należy sprawdzić, czy wartość zwracana jest ważna dla bezpiecznego połączenia.</span><span class="sxs-lookup"><span data-stu-id="d8319-936">If the remote host does not send a CloseNotify message, TLS considers this an error and a possible security breach, so checking the return value is important for a secure connection.</span></span> <span data-ttu-id="d8319-937">Parametr **WAIT_OPTION** może służyć do kontrolowania, jak długo usługa powinna czekać na odpowiedź przed zwróceniem kontroli do wątku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="d8319-937">The **wait_option** parameter can be used to control how long the service should wait for the response before returning control to the calling thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-938">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-938">Parameters</span></span>

- <span data-ttu-id="d8319-939">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-939">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="d8319-940">**WAIT_OPTION** Wskazuje, jak długo usługa powinna oczekiwać na odpowiedź z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-940">**wait_option** Indicates how long the service should wait for the response from the remote host.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-941">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-941">Return Values</span></span>

- <span data-ttu-id="d8319-942">**NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-942">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="d8319-943">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) nie otrzymał odpowiedzi z hosta zdalnego przed upływem limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="d8319-943">**NX_SECURE_TLS_NO_CLOSE_RESPONSE** (0x113) Did not receive a response from the remote host before timing out.</span></span>
- <span data-ttu-id="d8319-944">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie może przydzielić pakietu do wysłania wiadomości CloseNotify.</span><span class="sxs-lookup"><span data-stu-id="d8319-944">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Could not allocate a packet to send the CloseNotify message.</span></span>
- <span data-ttu-id="d8319-945">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) nie może wysłać komunikatu CloseNotify przez gniazdo TCP.</span><span class="sxs-lookup"><span data-stu-id="d8319-945">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) Could not send the CloseNotify message over the TCP socket.</span></span>
- <span data-ttu-id="d8319-946">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d8319-946">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-947">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-947">Allowed From</span></span>

<span data-ttu-id="d8319-948">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-948">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-949">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-949">Example</span></span>

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-950">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-950">See Also</span></span>

- <span data-ttu-id="d8319-951">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-951">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-952">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-952">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-953">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-953">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-954">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="d8319-954">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="d8319-955">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="d8319-955">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="d8319-956">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-956">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="d8319-957">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-957">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_packet_buffer_set"></a><span data-ttu-id="d8319-958">nx_secure_tls_session_packet_buffer_set</span><span class="sxs-lookup"><span data-stu-id="d8319-958">nx_secure_tls_session_packet_buffer_set</span></span>

<span data-ttu-id="d8319-959">Ustawianie buforu ponownego zestawu pakietów dla sesji bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-959">Set the packet reassembly buffer for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-960">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-960">Prototype</span></span>

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="d8319-961">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-961">Description</span></span>

<span data-ttu-id="d8319-962">Ta usługa kojarzy bufor ponownego asemblowania pakietów z sesją TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-962">This service associates a packet reassembly buffer to a TLS session.</span></span> <span data-ttu-id="d8319-963">Aby można było odszyfrować i przeanalizować przychodzące rekordy TLS, dane w każdym rekordzie muszą zostać zebrane z bazowych pakietów TCP.</span><span class="sxs-lookup"><span data-stu-id="d8319-963">In order to decrypt and parse incoming TLS records, the data in each record must be assembled from the underlying TCP packets.</span></span> <span data-ttu-id="d8319-964">Rekordy TLS mogą być maksymalnie 16 KB (zazwyczaj są znacznie mniejsze), więc mogą nie pasować do pojedynczego pakietu TCP.</span><span class="sxs-lookup"><span data-stu-id="d8319-964">TLS records can be up to 16KB in size (though typically are much smaller) so may not fit into a single TCP packet.</span></span>

<span data-ttu-id="d8319-965">Jeśli wiesz, że rozmiar komunikatu przychodzącego będzie mniejszy niż limit rekordu TLS 16 KB, rozmiar buforu może być mniejszy, ale w celu obsłużenia nieznanych danych przychodzących bufor powinien być wykonany tak jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="d8319-965">If you know the incoming message size will be smaller than the TLS record limit of 16KB, the buffer size can be made smaller, but in order to handle unknown incoming data the buffer should be made as large as possible.</span></span> <span data-ttu-id="d8319-966">Jeśli rekord przychodzący jest większy niż podany bufor, sesja TLS zakończy się błędem.</span><span class="sxs-lookup"><span data-stu-id="d8319-966">If an incoming record is larger than the supplied buffer, the TLS session will end with an error.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-967">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-967">Parameters</span></span>

- <span data-ttu-id="d8319-968">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-968">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="d8319-969">**buffer_ptr** Wskaźnik do bufora protokołu TLS, który ma być używany na potrzeby ponownego asemblowania pakietu.</span><span class="sxs-lookup"><span data-stu-id="d8319-969">**buffer_ptr** Pointer to buffer for TLS to use for packet reassembly.</span></span>
- <span data-ttu-id="d8319-970">**buffer_size** Rozmiar podanego buforu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="d8319-970">**buffer_size** Size of the supplied buffer in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-971">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-971">Return Values</span></span>

- <span data-ttu-id="d8319-972">**NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-972">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="d8319-973">**NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowy wskaźnik sesji buforu lub protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-973">**NX_INVALID_PARAMETERS** (0x4D) Invalid buffer or TLS session pointer.</span></span>
- <span data-ttu-id="d8319-974">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d8319-974">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-975">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-975">Allowed From</span></span>

<span data-ttu-id="d8319-976">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-976">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-977">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-977">Example</span></span>

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-978">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-978">See Also</span></span>

- <span data-ttu-id="d8319-979">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-979">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-980">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-980">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-981">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-981">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-982">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="d8319-982">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="d8319-983">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="d8319-983">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="d8319-984">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-984">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="d8319-985">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-985">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_protocol_version_override"></a><span data-ttu-id="d8319-986">nx_secure_tls_session_protocol_version_override</span><span class="sxs-lookup"><span data-stu-id="d8319-986">nx_secure_tls_session_protocol_version_override</span></span>

<span data-ttu-id="d8319-987">Zastąp domyślną wersję protokołu TLS dla sesji Secure TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-987">Override the default TLS protocol version for a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-988">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-988">Prototype</span></span>

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a><span data-ttu-id="d8319-989">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-989">Description</span></span>

<span data-ttu-id="d8319-990">Ta usługa zastępuje domyślną (najnowszą) wersję protokołu TLS używaną przez określoną sesję.</span><span class="sxs-lookup"><span data-stu-id="d8319-990">This service overrides the default (newest) TLS protocol version used by a particular session.</span></span> <span data-ttu-id="d8319-991">Pozwala to NetX Secure TLS na używanie starszej wersji protokołu TLS dla określonej sesji TLS bez wyłączania nowszych wersji protokołu TLS w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d8319-991">This enables NetX Secure TLS to use an older version of TLS for a specific TLS Session without disabling newer TLS versions at compile time.</span></span> <span data-ttu-id="d8319-992">Może to być przydatne w przypadku aplikacji, które mogą wymagać komunikacji z starszym hostem, który nie obsługuje najnowszej wersji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-992">This may be useful in applications that may need to communicate with an older host that does not support the newest version of TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8319-993">*Począwszy od wersji 5.11 SP3, NetX Secure TLS obsługuje RFC 7507 (patrz Uwaga poniżej), a wszystkie przesłonięcia do starszej wersji za pomocą tego interfejsu API spowoduje, że SCSV zostanie wysłane w komunikacie ClientHello. Jeśli serwer obsługuje nowszą wersję protokołu TLS, a rezerwa SCSV jest dołączana do komunikacie ClientHello, ten serwer przerywa uzgadnianie protokołu TLS z alertem "nieodpowiedni rezerwowy". SCSV jest wysyłana tylko wtedy, gdy przesłonięcia wersji jest starszą wersją protokołu TLS niż włączona (np. w przypadku zastąpienia wersji do protokołu TLS 1,2, nie zostanie wysłany żaden SCSV).*</span><span class="sxs-lookup"><span data-stu-id="d8319-993">*As of version 5.11SP3, NetX Secure TLS supports RFC 7507 (see note below) and any override to an older version with this API will result in a fallback SCSV being sent in the ClientHello. If the server supports a newer version of TLS and the fallback SCSV is included in the ClientHello, that server will abort the TLS handshake with an "Inappropriate Fallback" alert. The SCSV is only sent when the version override is an older version of TLS than is enabled (e.g. if you override the version to TLS 1.2, no SCSV will be sent).*</span></span>

<span data-ttu-id="d8319-994">Prawidłowe wartości parametru protocol_version to następujące makra: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1 i NX_SECURE_TLS_VERSION_TLS_1_2.</span><span class="sxs-lookup"><span data-stu-id="d8319-994">Valid values for the protocol_version parameter are the following macros: NX_SECURE_TLS_VERSION_TLS_1_0, NX_SECURE_TLS_VERSION_TLS_1_1, and NX_SECURE_TLS_VERSION_TLS_1_2.</span></span>

<span data-ttu-id="d8319-995">Makra NX_SECURE_TLS_DISABLE_TLS_1_1 i NX_SECURE_TLS_ENABLE_TLS_1_0 mogą służyć do kontrolowania wersji protokołu TLS, które są kompilowane w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8319-995">The macros NX_SECURE_TLS_DISABLE_TLS_1_1 and NX_SECURE_TLS_ENABLE_TLS_1_0 can be used to control the versions of TLS that are compiled into the application.</span></span> <span data-ttu-id="d8319-996">Protokół TLS w wersji 1,2 jest zawsze włączony.</span><span class="sxs-lookup"><span data-stu-id="d8319-996">TLS version 1.2 is always enabled.</span></span>

<span data-ttu-id="d8319-997">Należy pamiętać, że jeśli host zdalny nie obsługuje podanej wersji, połączenie zakończy się niepowodzeniem — tylko podana wersja przesłonięcia zostanie wynegocjowana przez NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-997">Note that if the remote host does not support the supplied version, the connection will fail – only the supplied override version will be negotiated by NetX Secure TLS.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8319-998">RFC 7507: SCSV rezerwowy protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-998">RFC 7507: TLS Fallback SCSV.</span></span> <span data-ttu-id="d8319-999">Ta Specyfikacja RFC została wprowadzona w celu wyeliminowania problemu zabezpieczeń, który był pierwotnie spowodowany przez serwery, które nieprawidłowo obsługiwały negocjowanie obniżenia poziomu protokołu, a zamiast tego odrzucają nieprawidłowe komunikaty komunikacie ClientHello.</span><span class="sxs-lookup"><span data-stu-id="d8319-999">This RFC was introduced to mitigate a security problem that was originally caused by servers that improperly handled protocol downgrade negotiation and instead rejected otherwise valid ClientHello messages.</span></span> <span data-ttu-id="d8319-1000">W przypadku próby zachowania zgodności z tymi starymi serwerami niektóre aplikacje klienckie TLS zaczęły ponawiać próbę niepowodzenia uzgadniania z i starszą wersją protokołu TLS (np. TLS 1,2 nie powiodło się, więc Wypróbuj protokół TLS 1,1).</span><span class="sxs-lookup"><span data-stu-id="d8319-1000">In an attempt to remain compatible with these old servers, some TLS client applications started to retry failed handshakes with and older TLS version (e.g. TLS 1.2 failed so try TLS 1.1).</span></span> <span data-ttu-id="d8319-1001">To obejście spowodowało jednak wprowadzenie nowego problemu — atakujący może wymusić obniżenie poziomu klienta, przez sztuczne wprowadzenie do błędu sieci lub pakietu, powodując niepowodzenie połączenia serwera — nawet wtedy, gdy serwer obsługiwał nowszą wersję protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1001">This workaround however introduced a new problem – an attacker could force a client to downgrade by artificially introducing a network or packet error causing the server connection to fail – even when the server supported the newer TLS version.</span></span> <span data-ttu-id="d8319-1002">W wyniku obniżenia poziomu do starszej wersji osoba atakująca może wykorzystać luki w tej wersji (protokół SSLv3<sup>21</sup> w szczególności jest to słabe dla ataku POODLE).</span><span class="sxs-lookup"><span data-stu-id="d8319-1002">By downgrading to an older version the attacker could exploit weaknesses in that version (SSLv3<sup>21</sup> in particular is weak to the POODLE attack).</span></span> <span data-ttu-id="d8319-1003">Aby zapobiec takiej sytuacji, w dokumencie RFC 7507 introdued "Fallback SCSV", pseudo ciphersuite<sup>22</sup> wysłany w komunikacie ClientHello, który POWIADAMIA serwer TLS, gdy klient TLS korzysta z wersji TLS, która nie jest wersją najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="d8319-1003">To prevent this situation, RFC 7507 introdued the "fallback SCSV," a pseudo-ciphersuite<sup>22</sup> sent in the ClientHello that notifies a TLS server when a TLS client is using a TLS version that is not the newest version it supports.</span></span> <span data-ttu-id="d8319-1004">W ten sposób serwer obsługujący nowszą wersję może odrzucić komunikacie ClientHello zawierający rezerwowy SCSV i zapobiec pomyślnym zaatakom na starszą wersję.</span><span class="sxs-lookup"><span data-stu-id="d8319-1004">This way, a server that supports a newer version can reject a ClientHello containing the fallback SCSV and prevent the downgrade attack from succeeding.</span></span>

21. <span data-ttu-id="d8319-1005">NetX Secure nie implementuje protokół SSLv3 z powodu istnienia znanych poważnych słabych wad, takich jak POODLE.</span><span class="sxs-lookup"><span data-stu-id="d8319-1005">NetX Secure does not implement SSLv3 due to the existence of known serious weaknesses such as POODLE.</span></span>

22. <span data-ttu-id="d8319-1006">Pseudo-ciphersuite lub SCSV (sygnalizujący wartość pakietu szyfrowania) to zarezerwowany numer ciphersuite, który jest używany do sygnalizowania z włączonymi implementacjami protokołu TLS o funkcjach, które nie były dostępne w starszych wersjach protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1006">A pseudo-ciphersuite, or SCSV (Signaling Cipher Suite Value), is a reserved ciphersuite number that is used to signal enabled TLS implementations about features that were not available in older TLS versions.</span></span> <span data-ttu-id="d8319-1007">SCSV Fallback i TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) są przykładami.</span><span class="sxs-lookup"><span data-stu-id="d8319-1007">The fallback SCSV and the TLS_EMPTY_RENEGOTIATION_INFO_SCSV (RFC 5746) are examples.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1008">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1008">Parameters</span></span>

- <span data-ttu-id="d8319-1009">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1009">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="d8319-1010">**protocol_version** Makro wersji protokołu TLS przeznaczone do użycia przez określoną wersję protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1010">**protocol_version** TLS version macro for the specific TLS version to use.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1011">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1011">Return Values</span></span>

- <span data-ttu-id="d8319-1012">Pomyślna zmiana stanu **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="d8319-1012">**NX_SUCCESS** (0x00) Successful state change.</span></span>
- <span data-ttu-id="d8319-1013">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1013">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="d8319-1014">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0X110) znana, ale nieobsługiwana wersja protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1014">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) Known but unsupported TLS version.</span></span>
- <span data-ttu-id="d8319-1015">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0X10F) Nieprawidłowa wersja protokołu.</span><span class="sxs-lookup"><span data-stu-id="d8319-1015">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) Invalid protocol version.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1016">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1016">Allowed From</span></span>

<span data-ttu-id="d8319-1017">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1017">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1018">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1018">Example</span></span>

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="d8319-1019">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1019">See Also</span></span>

- <span data-ttu-id="d8319-1020">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-1020">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-1021">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-1021">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_receive"></a><span data-ttu-id="d8319-1022">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-1022">nx_secure_tls_session_receive</span></span>

<span data-ttu-id="d8319-1023">Odbieranie danych z bezpiecznej sesji protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-1023">Receive data from a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1024">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1024">Prototype</span></span>

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d8319-1025">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1025">Description</span></span>

<span data-ttu-id="d8319-1026">Ta usługa odbiera dane z określonej aktywnej sesji protokołu TLS, obsługując odszyfrowywanie tych danych przed dostarczeniem ich do obiektu wywołującego w parametrze NX_PACKET.</span><span class="sxs-lookup"><span data-stu-id="d8319-1026">This service receives data from the specified active TLS session, handling the decryption of that data before providing it to the caller in the NX_PACKET parameter.</span></span> <span data-ttu-id="d8319-1027">Jeśli żadne dane nie są umieszczane w kolejce w określonej sesji, wywołanie zawiesza się na podstawie podanej opcji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="d8319-1027">If no data is queued in the specified session, the call suspends based on the supplied wait option.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8319-1028">*Jeśli NX_SUCCESS jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne.*</span><span class="sxs-lookup"><span data-stu-id="d8319-1028">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1029">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1029">Parameters</span></span>

- <span data-ttu-id="d8319-1030">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1030">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="d8319-1031">**packet_ptr** Wskaźnik do przydzielony wskaźnik pakietu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1031">**packet_ptr** Pointer to an allocated TLS packet pointer.</span></span>
- <span data-ttu-id="d8319-1032">**WAIT_OPTION** Wskazuje, jak długo usługa powinna czekać na pakiet z hosta zdalnego przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="d8319-1032">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1033">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1033">Return Values</span></span>

- <span data-ttu-id="d8319-1034">**NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1034">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="d8319-1035">**NX_NO_PACKET** (0X01) nie odebrano żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="d8319-1035">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="d8319-1036">**NX_NOT_CONNECTED** (0x38) podstawowy gniazdo TCP nie jest już połączony.</span><span class="sxs-lookup"><span data-stu-id="d8319-1036">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="d8319-1037">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) odebrany komunikat nie powiódł się podczas sprawdzania skrótu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="d8319-1037">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="d8319-1038">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) odebrana wiadomość zawierała nieznaną wersję protokołu w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="d8319-1038">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="d8319-1039">**NX_SECURE_TLS_ALERT_RECEIVED** (0X114) otrzymał alert protokołu TLS od hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-1039">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="d8319-1040">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d8319-1040">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="d8319-1041">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) dostarczona sesja TLS nie została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="d8319-1041">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1042">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1042">Allowed From</span></span>

<span data-ttu-id="d8319-1043">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1043">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1044">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1044">Example</span></span>

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a><span data-ttu-id="d8319-1045">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1045">See Also</span></span>

- <span data-ttu-id="d8319-1046">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-1046">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="d8319-1047">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-1047">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-1048">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-1048">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-1049">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-1049">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-1050">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="d8319-1050">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="d8319-1051">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="d8319-1051">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="d8319-1052">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="d8319-1052">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="d8319-1053">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-1053">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a><span data-ttu-id="d8319-1054">nx_secure_tls_session_renegotiate_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1054">nx_secure_tls_session_renegotiate_callback_set</span></span>

<span data-ttu-id="d8319-1055">Przypisanie wywołania zwrotnego, które zostanie wywołane na początku ponownej negocjacji sesji</span><span class="sxs-lookup"><span data-stu-id="d8319-1055">Assign a callback that will be invoked at the beginning of a session renegotiation</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1056">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1056">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a><span data-ttu-id="d8319-1057">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1057">Description</span></span>

<span data-ttu-id="d8319-1058">Ta usługa przypisuje wywołanie zwrotne do sesji TLS, które zostanie wywołane przy każdym odebraniu pierwszego komunikatu uzgadniania sesji z hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-1058">This service assigns a callback to a TLS session that will be invoked whenever the first message of a session renegotiation handshake is received from the remote host.</span></span>

<span data-ttu-id="d8319-1059">Funkcja wywołania zwrotnego służy jako powiadomienie do aplikacji, która rozpoczyna uzgadnianie renegocjacji — aplikacja może zdecydować się na zakończenie sesji TLS przez zwrócenie dowolnej wartości innej niż zero z wywołania zwrotnego, co spowoduje, że protokół TLS zakończy sesję TLS z błędem.</span><span class="sxs-lookup"><span data-stu-id="d8319-1059">The callback function is intended as a notification to the application that a renegotiation handshake is beginning – the application may choose to terminate the TLS session by returning any non-zero value from the callback which will cause TLS to end the TLS session with an error.</span></span> <span data-ttu-id="d8319-1060">Jeśli aplikacja chce kontynuować ponowną negocjację, wywołanie zwrotne powinno zwracać NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1060">If the application wishes to proceed with the renegotiation, the callback should return NX_SUCCESS.</span></span>

> [!NOTE]
> <span data-ttu-id="d8319-1061">*Ze względu na semantykę renegocjacji protokołu TLS wywołanie zwrotne zostanie wywołane dla NetX bezpiecznego protokołu TLS za każdym razem, gdy HelloRequest zostanie odebrany z serwera zdalnego, ale nie gdy Klient zainicjuje ponowną negocjację. Na serwerach Secure TLS NetX są wywoływane wywołania zwrotne za każdym razem, gdy zostanie odebrana ponowna negocjacja komunikacie ClientHello (wszystkie komunikacie ClientHello odebrane w kontekście aktywnej sesji protokołu TLS). Oznacza to, że wywołanie zwrotne zostanie wywołane niezależnie od tego, czy host zdalny lub lokalna aplikacja zainicjowała ponowną negocjację, ponieważ serwer TLS wyśle HelloRequest, do którego będzie odpowiadał Klient zdalny.*</span><span class="sxs-lookup"><span data-stu-id="d8319-1061">*Due to the semantics of TLS renegotiation, the callback will be invoked for NetX Secure TLS Clients whenever a HelloRequest is received from the remote server, but not when the client initiates the renegotiation. On NetX Secure TLS Servers, the callback will be invoked whenever a renegotiation ClientHello is received (any ClientHello received in the context of an active TLS session). This means that the callback will be invoked whether the remote host or the local application has initiated the renegotiation because the TLS server will send a HelloRequest to which the remote client will respond.*</span></span>

<span data-ttu-id="d8319-1062">NetX Secure TLS implementuje rozszerzenie Secure renegocjacji Inidication z RFC 5746, aby upewnić się, że uzgadniania renegocjacji nie podlegają atakom typu man-in-the-middle.</span><span class="sxs-lookup"><span data-stu-id="d8319-1062">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1063">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1063">Parameters</span></span>

- <span data-ttu-id="d8319-1064">**session_ptr** Wskaźnik na wystąpienie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1064">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="d8319-1065">**func_ptr** Wskaźnik do funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-1065">**func_ptr** Pointer to callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1066">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1066">Return Values</span></span>

- <span data-ttu-id="d8319-1067">**NX_SUCCESS** (0x00) — pomyślne przypisanie wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-1067">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="d8319-1068">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika dla funkcji wywołania zwrotnego lub sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1068">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer for the callback function or TLS session.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1069">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1069">Allowed From</span></span>

<span data-ttu-id="d8319-1070">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1070">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1071">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1071">Example</span></span>

```C
/* Simple callback notifying the user that a renegotiation is starting. */
ULONG tls_renegotiation_callback(NX_SECURE_TLS_SESSION *session)
{
    printf("Renegotiation initiated by remote host\n");

    return(NX_SUCCESS);
}

/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Set callback for renegotiation notification. */
status = nx_secure_tls_session_renegotiate_callback_set(&tls_session,
                                                tls_renegotiation_callback);
```

### <a name="see-also"></a><span data-ttu-id="d8319-1072">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1072">See Also</span></span>

- <span data-ttu-id="d8319-1073">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-1073">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-1074">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-1074">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-1075">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-1075">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="d8319-1076">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="d8319-1076">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="d8319-1077">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="d8319-1077">nx_secure_tls_session_renegotiate</span></span>

## <a name="nx_secure_tls_session_renegotiate"></a><span data-ttu-id="d8319-1078">nx_secure_tls_session_renegotiate</span><span class="sxs-lookup"><span data-stu-id="d8319-1078">nx_secure_tls_session_renegotiate</span></span>

<span data-ttu-id="d8319-1079">Inicjowanie uzgadniania sesji z hostem zdalnym</span><span class="sxs-lookup"><span data-stu-id="d8319-1079">Initiate a session renegotiation handshake with the remote host</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1080">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1080">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="d8319-1081">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1081">Description</span></span>

<span data-ttu-id="d8319-1082">Ta usługa *inicjuje uzgadnianie* sesji z połączonym hostem zdalnego protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1082">This service initiates a session *renegotiation* handshake with a connected remote TLS host.</span></span> <span data-ttu-id="d8319-1083">Ponowna negocjacja składa się z drugiego uzgadniania protokołu TLS w kontekście wcześniej ustanowionej sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1083">A renegotiation consists of a second TLS handshake within the context of a previously-established TLS session.</span></span> <span data-ttu-id="d8319-1084">Każdy nowy komunikat uzgadniania jest szyfrowany przy użyciu sesji TLS do momentu wygenerowania nowych kluczy sesji i wymiany komunikatów ChangeCipherSpec, podczas gdy nowe klucze są używane do szyfrowania wszystkich komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d8319-1084">Each of the new handshake messages is encrypted using the TLS session until new session keys are generated and ChangeCipherSpec messages are exchanged, at which time the new keys are used to encrypt all messages.</span></span>

<span data-ttu-id="d8319-1085">Ponowne negocjowanie można zainicjować w dowolnym momencie po ustanowieniu sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1085">A renegotiation can be initiated at any time once a TLS session is established.</span></span> <span data-ttu-id="d8319-1086">Jeśli zostanie podjęta próba ponownej negocjacji podczas uzgadniania protokołu TLS lub przed ustanowieniem sesji TLS, nie zostanie podjęta żadna akcja.</span><span class="sxs-lookup"><span data-stu-id="d8319-1086">If a renegotiation is attempted during a TLS handshake or before a TLS session is established no action will be taken.</span></span>

> [!NOTE]
> <span data-ttu-id="d8319-1087">*Całe uzgadnianie TLS zostanie wykonane, gdy ta usługa zostanie wywołana, co oznacza, że czas na ukończenie i zwrócony stan będą się różnić w zależności od bieżących ustawień protokołu TLS i parametrów sesji.*</span><span class="sxs-lookup"><span data-stu-id="d8319-1087">*An entire TLS handshake will be performed when this service is invoked so the time to completion and returned status will vary depending on the current TLS settings and session parameters.*</span></span>

<span data-ttu-id="d8319-1088">NetX Secure TLS implementuje rozszerzenie Secure renegocjacji Inidication z RFC 5746, aby upewnić się, że uzgadniania renegocjacji nie podlegają atakom typu man-in-the-middle.</span><span class="sxs-lookup"><span data-stu-id="d8319-1088">NetX Secure TLS implements the Secure Renegotiation Inidication Extension from RFC 5746 to ensure that renegotiation handshakes are not subject to man-in-the-middle attacks.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1089">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1089">Parameters</span></span>

- <span data-ttu-id="d8319-1090">**session_ptr** Wskaźnik na wystąpienie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1090">**session_ptr** Pointer to TLS Session instance.</span></span>
- <span data-ttu-id="d8319-1091">**WAIT_OPTION** Wskazuje, jak długo usługa powinna czekać na pakiet z hosta zdalnego przed zwróceniem.</span><span class="sxs-lookup"><span data-stu-id="d8319-1091">**wait_option** Indicates how long the service should wait for a packet from the remote host before returning.</span></span> <span data-ttu-id="d8319-1092">Jest ona przenoszona do wszystkich usług NetX w ramach protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1092">This is passed to all NetX services within TLS.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1093">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1093">Return Values</span></span>

- <span data-ttu-id="d8319-1094">**NX_SUCCESS** (0X00) pomyślne ponowne negocjowanie.</span><span class="sxs-lookup"><span data-stu-id="d8319-1094">**NX_SUCCESS** (0x00) Successful renegotiation.</span></span>
- <span data-ttu-id="d8319-1095">**NX_NO_PACKET** (0X01) nie odebrano żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="d8319-1095">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="d8319-1096">**NX_NOT_CONNECTED** (0x38) podstawowy gniazdo TCP nie jest już połączony.</span><span class="sxs-lookup"><span data-stu-id="d8319-1096">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="d8319-1097">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) odebrany komunikat nie powiódł się podczas sprawdzania skrótu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="d8319-1097">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) A received message failed an authentication hash check.</span></span>
- <span data-ttu-id="d8319-1098">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) odebrana wiadomość zawierała nieznaną wersję protokołu w nagłówku.</span><span class="sxs-lookup"><span data-stu-id="d8319-1098">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received message contained an unknown protocol version in its header.</span></span>
- <span data-ttu-id="d8319-1099">**NX_SECURE_TLS_ALERT_RECEIVED** (0X114) otrzymał alert protokołu TLS od hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-1099">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) Received a TLS alert from the remote host.</span></span>
- <span data-ttu-id="d8319-1100">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) lokalna lub zdalna sesja TLS jest nieaktywna, co uniemożliwia ponowne negocjowanie.</span><span class="sxs-lookup"><span data-stu-id="d8319-1100">**NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** (0x134) The local or remote TLS session is inactive, making renegotiation impossible.</span></span>
- <span data-ttu-id="d8319-1101">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) host zdalny nie dostarczył rozszerzenia SCSV lub bezpiecznego ponownego negocjowania, przez co nie można wykonać ponownej negocjacji.</span><span class="sxs-lookup"><span data-stu-id="d8319-1101">**NX_SECURE_TLS_RENEGOTIATION_FAILURE** (0x13A) The remote host did not provide either the SCSV or Secure Renegotiation Extension and thus renegotiation cannot be performed.</span></span>
- <span data-ttu-id="d8319-1102">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d8319-1102">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="d8319-1103">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) dostarczona sesja TLS nie została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="d8319-1103">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>
- <span data-ttu-id="d8319-1104">Alokacja podstawowego pakietu **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="d8319-1104">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) Underlying packet allocation failed.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1105">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1105">Allowed From</span></span>

<span data-ttu-id="d8319-1106">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1106">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1107">Example</span></span>

```C
/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Setup a client socket connection.  */
status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

/* Start the TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Send some data in the first TLS session. (Check “status” for errors…)*/
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Hello there!\r\n", 14, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);

/* Now renegotiate the session. */
status  = nx_secure_tls_session_renegotiate(&tls_session, NX_WAIT_FOREVER);

/* If status == NX_SUCCESS, new TLS session keys have been generated. */

/* Send some data in the new TLS session. This will be encrypted using the new
   keys. */
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Another message…\r\n", 18, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);
```

### <a name="see-also"></a><span data-ttu-id="d8319-1108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1108">See Also</span></span>

- <span data-ttu-id="d8319-1109">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-1109">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-1110">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-1110">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-1111">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-1111">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="d8319-1112">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="d8319-1112">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="d8319-1113">nx_secure_tls_session_renegotiation_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1113">nx_secure_tls_session_renegotiation_callback_set</span></span>

## <a name="nx_secure_tls_session_reset"></a><span data-ttu-id="d8319-1114">nx_secure_tls_session_reset</span><span class="sxs-lookup"><span data-stu-id="d8319-1114">nx_secure_tls_session_reset</span></span>

<span data-ttu-id="d8319-1115">Wyczyść i zresetuj bezpieczną sesję protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-1115">Clear out and reset a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1116">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1116">Prototype</span></span>

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a><span data-ttu-id="d8319-1117">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1117">Description</span></span>

<span data-ttu-id="d8319-1118">Ta usługa czyści sesję protokołu TLS i resetuje stan tak, jakby sesja została właśnie utworzona, a istniejący obiekt sesji TLS może zostać ponownie użyty dla nowej sesji.</span><span class="sxs-lookup"><span data-stu-id="d8319-1118">This service clears out a TLS session and resets the state as if the session had just been created so an existing TLS session object can be re-used for a new session.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1119">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1119">Parameters</span></span>

- <span data-ttu-id="d8319-1120">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1120">**session_ptr** Pointer to a TLS Session instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1121">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1121">Return Values</span></span>

- <span data-ttu-id="d8319-1122">**NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1122">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="d8319-1123">**NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowy wskaźnik sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1123">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="d8319-1124">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d8319-1124">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1125">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1125">Allowed From</span></span>

<span data-ttu-id="d8319-1126">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1126">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1127">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1127">Example</span></span>

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a><span data-ttu-id="d8319-1128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1128">See Also</span></span>

- <span data-ttu-id="d8319-1129">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-1129">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-1130">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-1130">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-1131">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-1131">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-1132">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="d8319-1132">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="d8319-1133">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="d8319-1133">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="d8319-1134">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-1134">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="d8319-1135">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-1135">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_send"></a><span data-ttu-id="d8319-1136">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="d8319-1136">nx_secure_tls_session_send</span></span>

<span data-ttu-id="d8319-1137">Wysyłanie danych za pomocą zabezpieczonej sesji protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-1137">Send data through a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1138">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1138">Prototype</span></span>

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d8319-1139">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1139">Description</span></span>

<span data-ttu-id="d8319-1140">Ta usługa wysyła dane w podanej NX_PACKET, przy użyciu określonej aktywnej sesji protokołu TLS i obsługującej szyfrowanie tych danych przed wysłaniem ich do hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-1140">This service sends data in the supplied NX_PACKET, using the specified active TLS session, and handling the encryption of that data before sending it to the remote host.</span></span> <span data-ttu-id="d8319-1141">Jeśli rozmiar okna o ostatnio anonsowanym odbiorniku jest mniejszy niż to żądanie, usługa opcjonalnie zawiesza się na podstawie określonych opcji oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="d8319-1141">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait options specified.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8319-1142">*Jeśli błąd nie zostanie zwrócony, aplikacja nie powinna zwolnić pakietu po tym wywołaniu. Wykonanie tej operacji spowoduje nieprzewidywalne wyniki, ponieważ sterownik sieciowy zwolni pakiet po przekazaniu.*</span><span class="sxs-lookup"><span data-stu-id="d8319-1142">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1143">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1143">Parameters</span></span>

- <span data-ttu-id="d8319-1144">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1144">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="d8319-1145">**packet_ptr** Wskaźnik na pakiet TLS zawierający dane do wysłania.</span><span class="sxs-lookup"><span data-stu-id="d8319-1145">**packet_ptr** Pointer to a TLS packet containing data to be sent.</span></span>
- <span data-ttu-id="d8319-1146">**WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli żądanie jest większe niż rozmiar okna odbiornika.</span><span class="sxs-lookup"><span data-stu-id="d8319-1146">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1147">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1147">Return Values</span></span>

- <span data-ttu-id="d8319-1148">**NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1148">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="d8319-1149">**NX_NO_PACKET** (0X01) nie odebrano żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="d8319-1149">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="d8319-1150">**NX_NOT_CONNECTED** (0x38) podstawowy gniazdo TCP nie jest już połączony.</span><span class="sxs-lookup"><span data-stu-id="d8319-1150">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="d8319-1151">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) nie można wysłać podstawowego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="d8319-1151">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) The underlying TCP socket send failed.</span></span>
- <span data-ttu-id="d8319-1152">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d8319-1152">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="d8319-1153">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) dostarczona sesja TLS nie została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="d8319-1153">**NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) The supplied TLS session was not initialized.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1154">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1154">Allowed From</span></span>

<span data-ttu-id="d8319-1155">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1155">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1156">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1156">Example</span></span>

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="d8319-1157">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1157">See Also</span></span>

- <span data-ttu-id="d8319-1158">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-1158">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="d8319-1159">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-1159">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-1160">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-1160">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-1161">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-1161">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="d8319-1162">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-1162">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-1163">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="d8319-1163">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="d8319-1164">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-1164">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="d8319-1165">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="d8319-1165">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="d8319-1166">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-1166">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_session_server_callback_set"></a><span data-ttu-id="d8319-1167">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1167">nx_secure_tls_session_server_callback_set</span></span>

<span data-ttu-id="d8319-1168">Skonfiguruj wywołanie zwrotne protokołu TLS do wywołania na początku uzgadniania serwera TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-1168">Set up a callback for TLS to invoke at the beginning of a TLS Server handshake</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1169">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1169">Prototype</span></span>

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a><span data-ttu-id="d8319-1170">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1170">Description</span></span>

<span data-ttu-id="d8319-1171">Ta usługa przypisuje wskaźnik funkcji do sesji TLS, która będzie wywoływała protokół TLS, gdy uzgadnianie serwera TLS odebrało komunikat komunikacie ClientHello.</span><span class="sxs-lookup"><span data-stu-id="d8319-1171">This service assigns a function pointer to a TLS session that TLS will invoke when a TLS Server handshake has received a ClientHello message.</span></span> <span data-ttu-id="d8319-1172">Funkcja wywołania zwrotnego umożliwia aplikacji przetwarzanie wszelkich rozszerzeń TLS z odebranego komunikatu komunikacie ClientHello, który wymaga wprowadzenia danych lub podejmowania decyzji.</span><span class="sxs-lookup"><span data-stu-id="d8319-1172">The callback function allows an application to process any TLS extensions from the received ClientHello message that require input or decision making.</span></span>

<span data-ttu-id="d8319-1173">Wywołanie zwrotne jest wykonywane z wywoływaniem bloku sterowania sesją TLS i tablicą obiektów NX_SECURE_TLS_HELLO_EXTENSION.</span><span class="sxs-lookup"><span data-stu-id="d8319-1173">The callback is executed with the invoking TLS session control block and an array of NX_SECURE_TLS_HELLO_EXTENSION objects.</span></span> <span data-ttu-id="d8319-1174">Tablica obiektów rozszerzeń jest przeznaczona do przekazywania do funkcji pomocnika, która będzie znajdować i analizować określone rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="d8319-1174">The array of extension objects is intended to be passed into a helper function that will find and parse a specific extension.</span></span> <span data-ttu-id="d8319-1175">Przykładowa funkcja pomocnicza, która analizuje rozszerzenia protokołu TLS podane w komunikatach Hello, znajduje się w temacie *nx_secure_tls_session_sni_extension_parse*.</span><span class="sxs-lookup"><span data-stu-id="d8319-1175">For an example helper function that parses TLS extensions provided in hello messages, see *nx_secure_tls_session_sni_extension_parse*.</span></span>

<span data-ttu-id="d8319-1176">Wywołania zwrotnego serwera można także użyć do wybrania aktywnego certyfikatu tożsamości przy użyciu *nx_secure_tls_active_certificate_set* dla serwera TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1176">The server callback may also be used to select the active identity certificate using *nx_secure_tls_active_certificate_set* for the TLS Server.</span></span> <span data-ttu-id="d8319-1177">Ta sytuacja najczęściej występuje w odpowiedzi na rozszerzenie Oznaczanie nazwy serwera (SNI), które umożliwia klientowi protokołu TLS wskazanie serwera, do którego próbuje się skontaktować.</span><span class="sxs-lookup"><span data-stu-id="d8319-1177">This will most often occur in response to a Server Name Indication (SNI) extension which allows a TLS Client to indicate which server it is attempting to contact.</span></span> <span data-ttu-id="d8319-1178">Aby uzyskać więcej informacji, zobacz odwołania do *nx_secure_tls_session_sni_extension_parse* i *nx_secure_tls_active_certificate_set* .</span><span class="sxs-lookup"><span data-stu-id="d8319-1178">See the references for *nx_secure_tls_session_sni_extension_parse* and *nx_secure_tls_active_certificate_set* for more information.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1179">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1179">Parameters</span></span>

- <span data-ttu-id="d8319-1180">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1180">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="d8319-1181">**func_ptr** Wskaźnik do funkcji wywołania zwrotnego serwera TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1181">**func_ptr** Pointer to the TLS Server callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1182">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1182">Return Values</span></span>

- <span data-ttu-id="d8319-1183">**NX_SUCCESS** (0X00) pomyślne alokacja wskaźnika funkcji.</span><span class="sxs-lookup"><span data-stu-id="d8319-1183">**NX_SUCCESS** (0x00) Successful allocation of Function pointer.</span></span>
- <span data-ttu-id="d8319-1184">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1184">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1185">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1185">Allowed From</span></span>

<span data-ttu-id="d8319-1186">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1186">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1187">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1187">Example</span></span>

```C
/* Application-supplied function to map server DNS name to a specific certificate
   ID. The certificate ID is supplied by the application when the certificate is
   added with nx_secure_tls_server_certificate_add. */
UINT application_find_id_by_dns_name(NX_SECURE_X509_DNS_NAME *dns_name)
{
    if(strncmp(dns_name->nx_secure_x509_dns_name, “server_name”,
               dns_name->nx_secure_x509_dns_name_length) == 0)
    {
        /* DNS name matches one we know, return it’s ID. */
        return(0x12);
    }

    /* Unknown DNS name, return 0 to indicate no matching ID found. */
    return(0);
}

/* Callback routine used to process ClientHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the client). */
ULONG tls_server_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;
UINT cert_id;
NX_SECURE_X509_CERT *certificate;


    /* Find and parse a Server Name Indication (SNI) extension. */
    status = nx_secure_tls_session_sni_extension_parse(session, extensions,
                                                       num_extensions, &dns_name);

    if(status != NX_SUCCESS && status != NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
        /* Parsed an invalid extension, return the error. */
        return(status);
    }

    if(status == NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
            /* SNI extension not found, just return success to use the default
               certificate. */
            return(NX_SUCCESS);
    }

    /* Find the application-supplied numeric identifier for the specified DNS
       name provided by the remote client. */
    cert_id = application_find_id_by_dns_name(&dns_name);

    /* If cert_id is 0, just use the default identity certificate added with
       nx_secure_tls_local_certificate_add. */
    if(cert_id != 0)
    {
        /* Application found a matching name, find the certificate in our
           store. */
        status = nx_secure_tls_server_certificate_find(tls_session, &certificate,
                                                       cert_id);

        if(status != NX_SUCCESS)
        {
            /* Didn’t find a valid certificate with the supplied ID. Return an
               error so TLS can shut down the handshake. */
            return(NX_SECURE_TLS_CERTIFICATE_NOT_FOUND);
        }

        /* Set the active identity certificate – the certificate should have been
           added to the local store at application start with
           nx_secure_tls_local_certificate_add. */
        nx_secure_tls_active_certificate_set(session, certificate);
    }

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_server_callback_set(tls_session,
                                                            server_callback);

        /* If status is NX_SUCCESS the callback was added and will be invoked
           immediately after a ClientHello message is received. */

        return(status);
}
```

### <a name="see-also"></a><span data-ttu-id="d8319-1188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1188">See Also</span></span>

- <span data-ttu-id="d8319-1189">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-1189">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-1190">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1190">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="d8319-1191">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1191">nx_secure_tls_active_certificate_set</span></span>
- <span data-ttu-id="d8319-1192">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="d8319-1192">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="d8319-1193">nx_secure_tls_server_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-1193">nx_secure_tls_server_certificate_add</span></span>
- <span data-ttu-id="d8319-1194">nx_secure_tls_server_certificate_find</span><span class="sxs-lookup"><span data-stu-id="d8319-1194">nx_secure_tls_server_certificate_find</span></span>

## <a name="nx_secure_tls_session_sni_extension_parse"></a><span data-ttu-id="d8319-1195">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="d8319-1195">nx_secure_tls_session_sni_extension_parse</span></span>

<span data-ttu-id="d8319-1196">Analizowanie rozszerzenia Oznaczanie nazwy serwera (SNI) otrzymanego z klienta TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-1196">Parse a Server Name Indication (SNI) extension received from a TLS Client</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1197">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1197">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="d8319-1198">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1198">Description</span></span>

<span data-ttu-id="d8319-1199">Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego sesji serwera TLS, dodawanego do sesji TLS przy użyciu nx_secure_tls_session_server_callback_set.</span><span class="sxs-lookup"><span data-stu-id="d8319-1199">This service is intended to be called from within a TLS Server session callback, added to a TLS session using nx_secure_tls_session_server_callback_set.</span></span> <span data-ttu-id="d8319-1200">Wywołanie zwrotne jest wywoływane po odebraniu komunikatu komunikacie ClientHello ze zdalnego klienta protokołu TLS i dostarcza tablicę dostępnych rozszerzeń (oraz liczbę rozszerzeń w tablicy).</span><span class="sxs-lookup"><span data-stu-id="d8319-1200">The callback is invoked following the reception of a ClientHello message from a remote TLS client and is supplied an array of available extensions (and the number of extensions in the array).</span></span> <span data-ttu-id="d8319-1201">Tę tablicę i jej długość można przesłać bezpośrednio do tej procedury, aby określić, czy istnieje rozszerzenie SNI (jeśli nie jest, zwracany jest NX_SECURE_TLS_EXTENSION_NOT_FOUND wskazujący, że klient nie zaznaczył rozszerzenia SNI (nie jest to błąd).</span><span class="sxs-lookup"><span data-stu-id="d8319-1201">That array and its length can be passed directly to this routine to determine if there is an SNI extension present – if not, NX_SECURE_TLS_EXTENSION_NOT_FOUND is returned indicating simply that the client opted not to provice the SNI extension (this is not an error).</span></span>

<span data-ttu-id="d8319-1202">Jeśli rozszerzenie SNI zostanie znalezione, nazwa DNS X. 509 dostarczana przez klienta TLS zostanie zwrócona w strukturze dns_name.</span><span class="sxs-lookup"><span data-stu-id="d8319-1202">If the SNI extension is found, the X.509 DNS name supplied by the TLS client is returned in the dns_name structure.</span></span> <span data-ttu-id="d8319-1203">Obecnie rozszerzenie SNI dostarcza tylko jeden wpis nazwy DNS, który może być używany przez serwer TLS w celu określenia certyfikatu tożsamości do wysłania do zdalnego klienta. \* \*</span><span class="sxs-lookup"><span data-stu-id="d8319-1203">Currently, the SNI extension only supplies a single DNS name entry, which may be used by the TLS server to determine which identity certificate to send to the remote client.\*\*</span></span>

<span data-ttu-id="d8319-1204">Struktura NX_SECURE_X509_DNS_NAME po prostu zawiera nazwę DNS jako ciąg UCHAR w polu *nx_secure_x509_dns_name* i długość ciągu nazwy w *nx_secure_x509_dns_name_length*.</span><span class="sxs-lookup"><span data-stu-id="d8319-1204">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="d8319-1205">Makro NX_SECURE_X509_DNS_NAME_MAX kontroluje rozmiar buforu nx_secure_x509_dns_name.</span><span class="sxs-lookup"><span data-stu-id="d8319-1205">The macro NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1206">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1206">Parameters</span></span>

- <span data-ttu-id="d8319-1207">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1207">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="d8319-1208">**rozszerzenia** Wskaźnik do tablicy rozszerzeń protokołu TLS Hello (od wywołania zwrotnego sesji).</span><span class="sxs-lookup"><span data-stu-id="d8319-1208">**extensions** Pointer to an array of TLS Hello extensions (from session callback).</span></span>
- <span data-ttu-id="d8319-1209">**num_extensions** Liczba rozszerzeń w tablicy (od wywołania zwrotnego sesji).</span><span class="sxs-lookup"><span data-stu-id="d8319-1209">**num_extensions** Number of extensions in array (from session callback).</span></span>
- <span data-ttu-id="d8319-1210">**dns_name** Zwróć nazwę DNS podaną w rozszerzeniu SNI.</span><span class="sxs-lookup"><span data-stu-id="d8319-1210">**dns_name** Return DNS name supplied in the SNI extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1211">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1211">Return Values</span></span>

- <span data-ttu-id="d8319-1212">**NX_SUCCESS** (0X00) pomyślne analizowanie rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d8319-1212">**NX_SUCCESS** (0x00) Successful parsing of the extension.</span></span>
- <span data-ttu-id="d8319-1213">**NX_PTR_ERROR** (0X07) Nieprawidłowa tablica rozszerzeń lub wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1213">**NX_PTR_ERROR** (0x07) Invalid extensions array or TLS session pointer.</span></span>
- <span data-ttu-id="d8319-1214">Nie znaleziono rozszerzenia SNI **NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136).</span><span class="sxs-lookup"><span data-stu-id="d8319-1214">**NX_SECURE_TLS_EXTENSION_NOT_FOUND** (0x136) SNI extension not found.</span></span>
- <span data-ttu-id="d8319-1215">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0X137) SNI format rozszerzenia jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d8319-1215">**NX_SECURE_TLS_SNI_EXTENSION_INVALID** (0x137) SNI extension format was invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1216">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1216">Allowed From</span></span>

<span data-ttu-id="d8319-1217">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1218">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1218">Example</span></span>

### <a name="see-also"></a><span data-ttu-id="d8319-1219">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1219">See Also</span></span>

- <span data-ttu-id="d8319-1220">nx_secure_tls_session_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1220">nx_secure_tls_session_server_callback_set</span></span>
- <span data-ttu-id="d8319-1221">nx_secure_tls_session_client_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1221">nx_secure_tls_session_client_callback_set</span></span>
- <span data-ttu-id="d8319-1222">nx_secure_tls_server_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1222">nx_secure_tls_server_callback_set</span></span>
- <span data-ttu-id="d8319-1223">nx_secure_tls_active_certificate_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1223">nx_secure_tls_active_certificate_set</span></span>

## <a name="nx_secure_tls_session_sni_extension_set"></a><span data-ttu-id="d8319-1224">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1224">nx_secure_tls_session_sni_extension_set</span></span>

<span data-ttu-id="d8319-1225">Ustaw nazwę DNS rozszerzenia Oznaczanie nazwy serwera (SNI) na wysyłanie do serwera zdalnego</span><span class="sxs-lookup"><span data-stu-id="d8319-1225">Set a Server Name Indication (SNI) extension DNS name to send to a remote Server</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1226">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1226">Prototype</span></span>

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a><span data-ttu-id="d8319-1227">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1227">Description</span></span>

<span data-ttu-id="d8319-1228">Ta usługa umożliwia aplikacji klienckiej TLS dostarczenie preferowanej nazwy serwera DNS do zdalnego serwera TLS przy użyciu rozszerzenia TLS Oznaczanie nazwy serwera (SNI).</span><span class="sxs-lookup"><span data-stu-id="d8319-1228">This service allows a TLS Client application to provide a preferred server DNS name to a remote TLS server using the Server Name Indication (SNI) TLS extension.</span></span> <span data-ttu-id="d8319-1229">Rozszerzenie SNI umożliwia serwerowi wybór właściwego certyfikatu tożsamości i parametrów na podstawie preferencji wskazanego serwera klienta.</span><span class="sxs-lookup"><span data-stu-id="d8319-1229">The SNI extension allows the server to select the proper identity certificate and parameters based on the client's indicated server preference.</span></span> <span data-ttu-id="d8319-1230">Rozszerzenie SNI obecnie obsługuje tylko pojedynczą nazwę DNS do wysłania, w związku z czym parametr nazwy pojedynczej.</span><span class="sxs-lookup"><span data-stu-id="d8319-1230">The SNI extension currently only supports a single DNS name to be sent, hence the singular name parameter.</span></span> <span data-ttu-id="d8319-1231">Parametr dns_name musi być zainicjowany przy użyciu *nx_secure_x509_dns_name_initialize* i będzie zawierać preferowany serwer klienta.</span><span class="sxs-lookup"><span data-stu-id="d8319-1231">The dns_name parameter must be initialized with *nx_secure_x509_dns_name_initialize* and will contain the client's preferred server.</span></span> <span data-ttu-id="d8319-1232">Aby cofnąć nazwę rozszerzenia, po prostu Wywołaj tę usługę przy użyciu wartości parametru "dns_name" NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="d8319-1232">To unset the extension name, simply call this service with a "dns_name" parameter value of NX_NULL.</span></span>

<span data-ttu-id="d8319-1233">Struktura NX_SECURE_X509_DNS_NAME po prostu zawiera nazwę DNS jako ciąg UCHAR w polu  *nx_secure_x509_dns_name* i długość ciągu nazwy w *nx_secure_x509_dns_name_length*.</span><span class="sxs-lookup"><span data-stu-id="d8319-1233">The NX_SECURE_X509_DNS_NAME structure simply contains the DNS name as a UCHAR string in the field  *nx_secure_x509_dns_name* and the length of the name string in *nx_secure_x509_dns_name_length*.</span></span> <span data-ttu-id="d8319-1234">Makro NX_SECURE_X509_DNS_NAME_MAX kontroluje rozmiar buforu nx_secure_x509_dns_name.</span><span class="sxs-lookup"><span data-stu-id="d8319-1234">The macro  NX_SECURE_X509_DNS_NAME_MAX controls the size of the nx_secure_x509_dns_name buffer.</span></span>

> [!NOTE]
> <span data-ttu-id="d8319-1235">*Ta procedura musi zostać wywołana przed wywołaniem nx_secure_tls_session_start lub komunikacie ClientHello nie będzie zawierać rozszerzenia SNI.*</span><span class="sxs-lookup"><span data-stu-id="d8319-1235">*This routine must be called before nx_secure_tls_session_start is invoked or the ClientHello will not contain the SNI extension.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1236">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1236">Parameters</span></span>

- <span data-ttu-id="d8319-1237">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1237">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="d8319-1238">**dns_name** Nazwa DNS dostarczana przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="d8319-1238">**dns_name** DNS name supplied by the application.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1239">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1239">Return Values</span></span>

- <span data-ttu-id="d8319-1240">**NX_SUCCESS** (0X00) pomyślne dodanie nazwy serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1240">**NX_SUCCESS** (0x00) Successful addition of DNS server name.</span></span>
- <span data-ttu-id="d8319-1241">**NX_PTR_ERROR** (0X07) Nieprawidłowa nazwa DNS lub wskaźnik sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1241">**NX_PTR_ERROR** (0x07) Invalid DNS name or TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1242">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1242">Allowed From</span></span>

<span data-ttu-id="d8319-1243">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1243">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1244">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1244">Example</span></span>

```C
#define TLS_SNI_SERVER_NAME “www.example.com”

NX_SECURE_X509_DNS_NAME dns_name;
NX_SECURE_TLS_SESSION client_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&client_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));


    /* Initialize the DNS server name we want to send in the SNI extension. */
    nx_secure_x509_dns_name_initialize(&dns_name, TLS_SNI_SERVER_NAME,
                                    strlen(TLS_SNI_SERVER_NAME));

    /* The SNI server name needs to be set prior to starting the TLS session. */
    nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);

   /* Start TLS session as normal. */
}
```

### <a name="see-also"></a><span data-ttu-id="d8319-1245">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1245">See Also</span></span>

- <span data-ttu-id="d8319-1246">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-1246">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-1247">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-1247">nx_secure_x509_dns_name_initialize</span></span>

## <a name="nx_secure_tls_session_start"></a><span data-ttu-id="d8319-1248">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-1248">nx_secure_tls_session_start</span></span>

<span data-ttu-id="d8319-1249">Rozpocznij sesję bezpiecznego protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-1249">Start a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1250">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1250">Prototype</span></span>

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d8319-1251">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1251">Description</span></span>

<span data-ttu-id="d8319-1252">Ta usługa uruchamia sesję protokołu TLS przy użyciu dostarczonego bloku kontroli sesji TLS i połączonego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="d8319-1252">This service starts a TLS session using the supplied TLS session control block and a connected TCP socket.</span></span> <span data-ttu-id="d8319-1253">Połączenie TCP musi być już zakończone po pomyślnym wywołaniu do nx_tcp_client_socket_connect lub nx_tcp_server_socket_accept.</span><span class="sxs-lookup"><span data-stu-id="d8319-1253">The TCP connection must already be complete following a successful call to either nx_tcp_client_socket_connect or nx_tcp_server_socket_accept.</span></span>

<span data-ttu-id="d8319-1254">Ta usługa określi typ sesji TLS (klienta lub serwera) z gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="d8319-1254">This service will determine the type of TLS session (Client or Server) from the TCP socket.</span></span>

<span data-ttu-id="d8319-1255">Opcja oczekiwania definiuje, jak działa usługa, gdy uzgadnianie TLS jest w toku.</span><span class="sxs-lookup"><span data-stu-id="d8319-1255">The wait option defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1256">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1256">Parameters</span></span>

- <span data-ttu-id="d8319-1257">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1257">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="d8319-1258">**tcp_socket_ptr** Wskaźnik do połączonego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="d8319-1258">**tcp_socket_ptr** Pointer to a connected TCP socket.</span></span>
- <span data-ttu-id="d8319-1259">**WAIT_OPTION** Definiuje sposób zachowania usługi podczas uzgadniania protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1259">**wait_option** Defines how the service behaves while the TLS handshake is in progress.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1260">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1260">Return Values</span></span>

- <span data-ttu-id="d8319-1261">**NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1261">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="d8319-1262">**NX_NOT_CONNECTED** (0x38) podstawowy gniazdo TCP nie jest już połączony.</span><span class="sxs-lookup"><span data-stu-id="d8319-1262">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="d8319-1263">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) otrzymany typ komunikatu TLS jest niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="d8319-1263">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="d8319-1264">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) szyfr dostarczony przez hosta zdalnego nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="d8319-1264">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="d8319-1265">Przetwarzanie komunikatu **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) podczas UZGADNIANIA protokołu TLS nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="d8319-1265">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="d8319-1266">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) komunikat przychodzący nie powiódł się podczas sprawdzania skrótu Mac.</span><span class="sxs-lookup"><span data-stu-id="d8319-1266">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a hash MAC check.</span></span>
- <span data-ttu-id="d8319-1267">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) nie można wysłać podstawowego gniazda TCP.</span><span class="sxs-lookup"><span data-stu-id="d8319-1267">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="d8319-1268">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) komunikat przychodzący miał nieprawidłową długość pola.</span><span class="sxs-lookup"><span data-stu-id="d8319-1268">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="d8319-1269">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) odebrana wiadomość ChangeCipherSpec jest niepoprawna.</span><span class="sxs-lookup"><span data-stu-id="d8319-1269">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="d8319-1270">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) przychodzący certyfikat TLS nie nadaje się do identyfikacji serwera zdalnego protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1270">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="d8319-1271">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) szyfrowanie klucza publicznego dostarczone przez hosta zdalnego nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d8319-1271">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="d8319-1272">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) host zdalny nie wskazywał ciphersuites, które są obsługiwane przez stos NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1272">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="d8319-1273">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) odebrany komunikat TLS miał nieznaną wersję protokołu TLS w jego nagłówku.</span><span class="sxs-lookup"><span data-stu-id="d8319-1273">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="d8319-1274">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) odebrany komunikat TLS miał znaną, ale nieobsługiwaną wersję protokołu TLS w jego nagłówku.</span><span class="sxs-lookup"><span data-stu-id="d8319-1274">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="d8319-1275">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) nie powiodła się wewnętrzna alokacja pakietu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1275">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="d8319-1276">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) host zdalny dostarczył nieprawidłowy certyfikat.</span><span class="sxs-lookup"><span data-stu-id="d8319-1276">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="d8319-1277">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) host zdalny wysłał alert wskazujący błąd i zakończenie sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1277">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="d8319-1278">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) wpis w tabeli ciphersuite ma wskaźnik funkcji o wartości null.</span><span class="sxs-lookup"><span data-stu-id="d8319-1278">**NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) An entry in the ciphersuite table had a NULL function pointer.</span></span>
- <span data-ttu-id="d8319-1279">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) zdalna komunikacie CLIENTHELLO protokołu TLS obejmowała rezerwowe SCSV andattempted w wersji rezerwowej.</span><span class="sxs-lookup"><span data-stu-id="d8319-1279">**NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** (0x146) A remote TLS ClientHello included the fallback SCSV andattempted a version fallback.</span></span>
- <span data-ttu-id="d8319-1280">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d8319-1280">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1281">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1281">Allowed From</span></span>

<span data-ttu-id="d8319-1282">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1282">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1283">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1283">Example</span></span>

```C
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Initialize the TLS session structure. */
nx_secure_tls_session_create(&tls_session,
                              &nx_crypto_tls_ciphers,
                              crypto_metadata,
                              sizeof(crypto_metadata));

/* Setup the TLS packet reassembly buffer. */
status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                 sizeof(tls_packet_buffer));

/* Initialize a certificate for the TLS server. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data, 500,
NX_NULL, 0, private_key, 64);

/* If status is NX_SUCCESS, certificate is initialized. */

/* Add the certificate a local certificate to identify this TLS server. */
status = nx_secure_tls_add_local_certificate(&tls_session, &certificate);

/* If status is NX_SUCCESS, certificate was added successfully. */

/* Create and start a TCP socket as a server. */
/* NOTE: This assumes an IP instance called “ip_0” has already been created. */

/* Create a TCP server socket on the previously created IP instance, with normal
   delivery, IP fragmentation enabled, default time to live, a 8192-byte receive
   window, no urgent callback routine, and the "client_disconnect" routine to
   handle disconnection initiated from the other end of the connection.  */
status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket", NX_IP_NORMAL,
                               NX_FRAGMENT_OKAY, NX_IP_TIME_TO_LIVE, 8192, NX_NULL,
                               NX_NULL);

/* If status is NX_SUCCESS, the TCP socket was created successfully. */

/* Start up a TCP server socket by listening on port 443 with a listen queue of
   size 5. */
status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

/* Application main loop. */
while(1)
{
        /* Accept incoming requests on the TCP socket. */
        status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

        /* At this point, the TCP socket should be established (but not the TLS
        session yet). */

        /* Start the TLS session on our active TCP socket. */
        status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                             NX_WAIT_FOREVER);

        /* At this point, if status is NX_SUCCESS, the TLS session has been
           established.  Application may now send/receive data through this
           channel. */

        /* Send and receive data using the TLS session. */
        /* Allocate TLS packets using nx_secure_tls_packet_allocate, write data with
           nx_packet_data_append, read data with nx_packet_data_extract_offset. */

        /* Send TLS data. */
        nx_secure_tls_session_send(&tls_session, &send_packet, NX_WAIT_FOREVER);

        nx_secure_tls_session_receive(&tls_session, &receive_packet_ptr,
        NX_WAIT_FOREVER);


        /* Once all application data is sent/received, end the TLS session. */
        status = nx_secure_tls_session_end(&tls_session);

        /* If status is NX_SUCCESS, the TLS session has been closed properly. */

        /* Now disconnect the TCP server socket from the client.  */
        nx_tcp_socket_disconnect(&tcp_socket, 200);

        /* Unaccept the TCP server socket.  Note that unaccept is called even if
           disconnect or accept fails.  */
        nx_tcp_server_socket_unaccept(&tcp_socket);

        /* Setup server socket for listening with this socket again.  */
        nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
}

/* When the server application is shut down, clean up the TLS session. */
nx_secure_tls_session_delete(&tls_session);

/* Finally, clean up the TCP socket as well. */
nx_tcp_socket_delete(&tcp_socket);
```

### <a name="see-also"></a><span data-ttu-id="d8319-1284">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1284">See Also</span></span>

- <span data-ttu-id="d8319-1285">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-1285">nx_tcp_socket_receive</span></span>
- <span data-ttu-id="d8319-1286">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-1286">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-1287">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-1287">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-1288">nx_secure_tls_session_send</span><span class="sxs-lookup"><span data-stu-id="d8319-1288">nx_secure_tls_session_send</span></span>
- <span data-ttu-id="d8319-1289">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="d8319-1289">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="d8319-1290">nx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-1290">nx_secure_tls_session_receive</span></span>
- <span data-ttu-id="d8319-1291">nx_secure_tls_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-1291">nx_secure_tls_packet_allocate</span></span>
- <span data-ttu-id="d8319-1292">nx_secure_tls_session_end</span><span class="sxs-lookup"><span data-stu-id="d8319-1292">nx_secure_tls_session_end</span></span>
- <span data-ttu-id="d8319-1293">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-1293">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-1294">nx_tcp_socket_accept</span><span class="sxs-lookup"><span data-stu-id="d8319-1294">nx_tcp_socket_accept</span></span>
- <span data-ttu-id="d8319-1295">nx_tcp_socket_listen</span><span class="sxs-lookup"><span data-stu-id="d8319-1295">nx_tcp_socket_listen</span></span>
- <span data-ttu-id="d8319-1296">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="d8319-1296">nx_tcp_socket_disconnect</span></span>
- <span data-ttu-id="d8319-1297">nx_tcp_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="d8319-1297">nx_tcp_socket_unaccept</span></span>
- <span data-ttu-id="d8319-1298">nx_tcp_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="d8319-1298">nx_tcp_socket_relisten</span></span>
- <span data-ttu-id="d8319-1299">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="d8319-1299">nx_tcp_socket_delete</span></span>
- <span data-ttu-id="d8319-1300">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-1300">nx_packet_allocate</span></span>
- <span data-ttu-id="d8319-1301">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="d8319-1301">nx_packet_data_append</span></span>
- <span data-ttu-id="d8319-1302">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="d8319-1302">nx_packet_data_extract_offset</span></span>

## <a name="nx_secure_tls_session_time_function_set"></a><span data-ttu-id="d8319-1303">nx_secure_tls_session_time_function_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1303">nx_secure_tls_session_time_function_set</span></span>

<span data-ttu-id="d8319-1304">Przypisywanie funkcji sygnatury czasowej do NetX bezpiecznej sesji TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-1304">Assign a timestamp function to a NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1305">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1305">Prototype</span></span>

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a><span data-ttu-id="d8319-1306">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1306">Description</span></span>

<span data-ttu-id="d8319-1307">Ta funkcja konfiguruje wskaźnik funkcji, który zostanie wywołany przez protokół TLS, gdy musi on uzyskać bieżący czas, który jest używany w różnych komunikatach uzgadniania protokołu TLS i w celu weryfikacji certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d8319-1307">This function sets up a function pointer that TLS will invoke when it needs to get the current time, which is used in various TLS handshake messages and for verification of certificates.</span></span>

<span data-ttu-id="d8319-1308">Oczekiwane jest, że funkcja zwraca bieżącą wartość GMT w formacie systemu UNIX 32-bitowym (sekundy od północy od 1 stycznia 1970, czas UTC, w sekundach), zgodnie z wymaganiami komunikacie ClientHello zawartymi w specyfikacji TLS RFC 5246.</span><span class="sxs-lookup"><span data-stu-id="d8319-1308">The function is expected to return the current GMT in UNIX 32-bit format (seconds since the midnight starting Jan 1, 1970, UTC, ignoring leap seconds), as per the ClientHello requirements in the TLS RFC 5246.</span></span>

<span data-ttu-id="d8319-1309">Jeśli nie zostanie przypisana żadna funkcja znacznika czasu, zostanie użyta wartość 0 dla sygnatury czasowej w uzgadnianiu TLS, a sprawdzanie wygaśnięcia certyfikatu nie będzie działać.</span><span class="sxs-lookup"><span data-stu-id="d8319-1309">If no timestamp function is assigned, a value of 0 for the timestamp in the TLS handshake will be used and certificate expiration checking will not work.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1310">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1310">Parameters</span></span>

- <span data-ttu-id="d8319-1311">**session_ptr** Wskaźnik do wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1311">**session_ptr** Pointer to a TLS Session instance.</span></span>
- <span data-ttu-id="d8319-1312">**time_func_ptr** Wskaźnik do funkcji zwracającej bieżący czas (GMT) w formacie systemu UNIX 32-bitowym.</span><span class="sxs-lookup"><span data-stu-id="d8319-1312">**time_func_ptr** Pointer to a function that returns the current time (GMT) in UNIX 32-bit format.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1313">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1313">Return Values</span></span>

- <span data-ttu-id="d8319-1314">**NX_SUCCESS** (0X00) pomyślne INICJOWANIE sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1314">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="d8319-1315">**NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowy wskaźnik sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1315">**NX_INVALID_PARAMETERS** (0x4D) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="d8319-1316">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d8319-1316">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1317">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1317">Allowed From</span></span>

<span data-ttu-id="d8319-1318">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1318">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1319">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1319">Example</span></span>

```C
/* This function returns a 32-bit UNIX-style representation of the current GMT
   time. */
ULONG get_gmt_time(void)
{
ULONG time_value;

   /* Platform-specific time calculation goes here… */

   return(time_value);
}

/* Reset a TLS session.  */
status =  nx_secure_tls_timestamp_function_set(&tls_session, get_gmt_time);


/* If status is NX_SUCCESS the function was successfully added.*/
```

### <a name="see-also"></a><span data-ttu-id="d8319-1320">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1320">See Also</span></span>

- <span data-ttu-id="d8319-1321">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-1321">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-1322">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-1322">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-1323">nx_secure_tls_session_start</span><span class="sxs-lookup"><span data-stu-id="d8319-1323">nx_secure_tls_session_start</span></span>
- <span data-ttu-id="d8319-1324">nx_secure_tls_session_delete</span><span class="sxs-lookup"><span data-stu-id="d8319-1324">nx_secure_tls_session_delete</span></span>
- <span data-ttu-id="d8319-1325">nx_secure_tls_session_sendnx_secure_tls_session_receive</span><span class="sxs-lookup"><span data-stu-id="d8319-1325">nx_secure_tls_session_sendnx_secure_tls_session_receive</span></span>
- <span data-ttu-id="d8319-1326">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-1326">nx_secure_tls_session_create</span></span>

## <a name="nx_secure_tls_trusted_certificate_add"></a><span data-ttu-id="d8319-1327">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-1327">nx_secure_tls_trusted_certificate_add</span></span>

<span data-ttu-id="d8319-1328">Dodaj zaufany certyfikat do NetX bezpiecznej sesji TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-1328">Add trusted certificate to NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1329">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1329">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a><span data-ttu-id="d8319-1330">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1330">Description</span></span>

<span data-ttu-id="d8319-1331">Ta usługa dodaje zainicjowane wystąpienie struktury NX_SECURE_X509_CERT do sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1331">This service adds an initialized NX_SECURE_X509_CERT structure instance to a TLS session.</span></span> <span data-ttu-id="d8319-1332">Ten certyfikat jest używany przez stos TLS do weryfikowania certyfikatów dostarczonych przez hosta zdalnego podczas uzgadniania protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1332">This certificate is used by the TLS stack to verify certificates supplied by the remote host during the TLS handshake.</span></span>

<span data-ttu-id="d8319-1333">Certyfikaty zaufane są wymagane dla trybu klienta protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1333">Trusted certificates are required for TLS Client mode.</span></span>

<span data-ttu-id="d8319-1334">Certyfikaty zaufane są wymagane tylko w trybie serwera TLS, jeśli jest włączone uwierzytelnianie certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="d8319-1334">Trusted certificates are only required for TLS Server mode if client certificate authentication is enabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1335">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1335">Parameters</span></span>

- <span data-ttu-id="d8319-1336">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1336">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="d8319-1337">**certificate_ptr** Wskaźnik do zainicjowane wystąpienie certyfikatu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1337">**certificate_ptr** Pointer to an initialized TLS Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1338">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1338">Return Values</span></span>

- <span data-ttu-id="d8319-1339">**NX_SUCCESS** (0X00) pomyślne dodanie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-1339">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="d8319-1340">**NX_INVALID_PARAMETERS** (0x4D) próbował dodać nieprawidłowy certyfikat.</span><span class="sxs-lookup"><span data-stu-id="d8319-1340">**NX_INVALID_PARAMETERS** (0x4D) Tried to add an invalid certificate.</span></span>
- <span data-ttu-id="d8319-1341">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1341">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1342">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1342">Allowed From</span></span>

<span data-ttu-id="d8319-1343">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1343">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1344">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1344">Example</span></span>

```C
/* Initialize certificate structure. */
status = nx_secure_x509_certificate_initialize(&certificate, certificate_data,
                                               certificate_buffer,
                                               sizeof(certificate_buffer), 500,
                                               private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-1345">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1345">See Also</span></span>

- <span data-ttu-id="d8319-1346">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-1346">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-1347">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-1347">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-1348">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-1348">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-1349">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="d8319-1349">nx_secure_tls_trusted_certificate_remove</span></span>

## <a name="nx_secure_tls_trusted_certificate_remove"></a><span data-ttu-id="d8319-1350">nx_secure_tls_trusted_certificate_remove</span><span class="sxs-lookup"><span data-stu-id="d8319-1350">nx_secure_tls_trusted_certificate_remove</span></span>

<span data-ttu-id="d8319-1351">Usuń zaufany certyfikat z bezpiecznej sesji protokołu TLS NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-1351">Remove trusted certificate from NetX Secure TLS Session</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1352">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1352">Prototype</span></span>

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a><span data-ttu-id="d8319-1353">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1353">Description</span></span>

<span data-ttu-id="d8319-1354">Ta usługa usuwa zaufany certyfikat z sesji TLS, który został utworzony w polu Nazwa pospolita w certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="d8319-1354">This service removes a trusted certificate from a TLS session, keyed on the Common Name field in the certificate.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1355">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1355">Parameters</span></span>

- <span data-ttu-id="d8319-1356">**session_ptr** Wskaźnik do wcześniej utworzonego wystąpienia sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1356">**session_ptr** Pointer to a previously created TLS Session instance.</span></span>
- <span data-ttu-id="d8319-1357">**common_name** Wartość nazwy pospolitej certyfikatu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="d8319-1357">**common_name** The Common Name value of the certificate to be removed.</span></span>
- <span data-ttu-id="d8319-1358">**common_name_length** Długość ciągu nazwy pospolitej.</span><span class="sxs-lookup"><span data-stu-id="d8319-1358">**common_name_length** The length of the Common Name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1359">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1359">Return Values</span></span>

- <span data-ttu-id="d8319-1360">**NX_SUCCESS** (0X00) pomyślne dodanie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-1360">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="d8319-1361">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik sesji protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1361">**NX_PTR_ERROR** (0x07) Invalid TLS session pointer.</span></span>
- <span data-ttu-id="d8319-1362">Nie znaleziono certyfikatu **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119).</span><span class="sxs-lookup"><span data-stu-id="d8319-1362">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) Certificate was not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1363">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1363">Allowed From</span></span>

<span data-ttu-id="d8319-1364">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1364">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1365">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1365">Example</span></span>

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-1366">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1366">See Also</span></span>

- <span data-ttu-id="d8319-1367">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-1367">nx_secure_x509_certificate_initialize</span></span>
- <span data-ttu-id="d8319-1368">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-1368">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-1369">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-1369">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-1370">nx_secure_tls_trusted_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-1370">nx_secure_tls_trusted_certificate_add</span></span>

## <a name="nx_secure_x509_certificate_initialize"></a><span data-ttu-id="d8319-1371">nx_secure_x509_certificate_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-1371">nx_secure_x509_certificate_initialize</span></span>

<span data-ttu-id="d8319-1372">Zainicjuj certyfikat X. 509 dla usługi NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-1372">Initialize X.509 Certificate for NetX Secure TLS</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1373">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1373">Prototype</span></span>

```C
UINT  nx_secure_x509_certificate_initialize(
                  NX_SECURE_X509_CERT *certificate_ptr,
                  const UCHAR *certificate_data,
                  USHORT certificate_data_length,
                  UCHAR *raw_data_buffer,
                  USHORT buffer_size,
                  const UCHAR *private_key_data,
                  USHORT private_key_data_length,
                  UINT private_key_type);
```

### <a name="description"></a><span data-ttu-id="d8319-1374">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1374">Description</span></span>

<span data-ttu-id="d8319-1375">Ta usługa inicjuje strukturę NX_SECURE_X509_CERT z certyfikatu cyfrowego X. 509 kodowanego binarnie do użycia w sesji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1375">This service initializes an NX_SECURE_X509_CERT structure from a binary-encoded X.509 digital certificate for use in a TLS session.</span></span>

<span data-ttu-id="d8319-1376">Dane certyfikatu **muszą** być prawidłowym certyfikatem cyfrowym X. 509 w formacie binarnym SZYFROWANYm algorytmem DER.</span><span class="sxs-lookup"><span data-stu-id="d8319-1376">The certificate data **must** be a valid X.509 digital certificate in DER-encoded binary format.</span></span> <span data-ttu-id="d8319-1377">Dane mogą zostać określone z dowolnego źródła (np. systemu plików, skompilowanego stałego buforu itp.), o ile jest dostępny wskaźnik UCHAR do tych danych.</span><span class="sxs-lookup"><span data-stu-id="d8319-1377">The data can some from any source (e.g. file system, compiled constant buffer, etc.) as long as a UCHAR pointer to that data is provided.</span></span>

<span data-ttu-id="d8319-1378">Parametr *raw_data_buffer* i jego rozmiar są opcjonalnymi parametrami, które określają dedykowany bufor, do którego kopiowane są dane certyfikatu przed rozpoczęciem analizy.</span><span class="sxs-lookup"><span data-stu-id="d8319-1378">The *raw_data_buffer* parameter and its size are optional parameters that specify a dedicated buffer into which the certificate data is copied before parsing.</span></span> <span data-ttu-id="d8319-1379">Jeśli raw_data_buffer jest przenoszona jako NX_NULL, struktura NX_SECURE_X509_CERT będzie wskazywała bezpośrednio na tablicę certificate_data (buffer_size w tym przypadku jest ignorowana).</span><span class="sxs-lookup"><span data-stu-id="d8319-1379">If raw_data_buffer is passed as NX_NULL then the NX_SECURE_X509_CERT structure will point directly into the certificate_data array (buffer_size is ignored in this case).</span></span> <span data-ttu-id="d8319-1380">Jeśli raw_data_buffer jest przenoszona jako NX_NULL ***, nie należy modyfikować*** danych wskazywanych przez wskaźnik certificate_data lub przetwarzanie certyfikatu prawdopodobnie zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="d8319-1380">If raw_data_buffer is passed as NX_NULL, ***do not*** modify the data pointed to by the certificate_data pointer or certificate processing will likely fail!</span></span>

<span data-ttu-id="d8319-1381">Parametr klucza prywatnego dotyczy lokalnych certyfikatów tożsamości — klucz prywatny jest używany przez serwery do odszyfrowywania danych klucza przychodzącego z klienta (szyfrowany przy użyciu klucza publicznego serwera) oraz przez klientów, aby zweryfikować swoją tożsamość na serwerze, gdy serwer żąda certyfikatu klienta.</span><span class="sxs-lookup"><span data-stu-id="d8319-1381">The private key parameter is for local identity certificates – the private key is used by servers to decrypt the incoming key data from a client (encrypted using the server's public key) and by clients to verify their identity to a server when the server requests a client certificate.</span></span> <span data-ttu-id="d8319-1382">Dodanie klucza prywatnego z tym interfejsem API spowoduje automatyczne oznaczenie skojarzonego certyfikatu jako certyfikatu tożsamości dla aplikacji TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1382">Adding a private key with this API will automatically mark the associated certificate as being an identity certificate for a TLS application.</span></span> <span data-ttu-id="d8319-1383">W przypadku inicjowania certyfikatów do innych celów (np. zaufanych magazynów) parametr *private_key_data* powinien zostać przekazana jako wartość NULL, *private_key_data_length* jako 0 i *private_key_type* powinien zostać przesłany jako NX_SECURE_X509_KEY_TYPE_NONE.</span><span class="sxs-lookup"><span data-stu-id="d8319-1383">When initializing certificates for other purposes (e.g. the trusted store), the *private_key_data* parameter should be passed as NULL, the *private_key_data_length* as 0, and the *private_key_type* should be passed as NX_SECURE_X509_KEY_TYPE_NONE.</span></span>

<span data-ttu-id="d8319-1384">Parametr *private_key_type* wskazuje formatowanie klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-1384">The *private_key_type* parameter indicates the formatting of the private key.</span></span> <span data-ttu-id="d8319-1385">Na przykład jeśli klucz prywatny jest zakodowanym algorytmem DER w formacie PKCS # 1 — kluczem prywatnym RSA, private_key_type powinny być przesyłane jako NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, typ znany NetX Secure, który zostanie natychmiast przeanalizowany i zapisany do późniejszego użycia.</span><span class="sxs-lookup"><span data-stu-id="d8319-1385">For example, if the private key is a DER-encoded PKCS#1-format RSA private key, the private_key_type should be passed as NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER, a type known to NetX Secure which will be parsed immediately and saved for later use.</span></span>

<span data-ttu-id="d8319-1386">Private_key_type obsługuje również typy kluczy zdefiniowane przez użytkownika<sup>23</sup> dla platform i aplikacji, które mają określone formaty kluczy lub inne wymagania.</span><span class="sxs-lookup"><span data-stu-id="d8319-1386">The private_key_type also supports user-defined key types<sup>23</sup> for platforms and applications that have specific key formats or other needs.</span></span> <span data-ttu-id="d8319-1387">Na przykład aparat szyfrowania sprzętowego może używać określonego formatu, który nie jest rozpoznawany przez NetX bezpieczne oprogramowanie, lub klucz prywatny może być zaszyfrowany lub reprezentowany przez token kryptograficzny, tak jak w przypadku sprzętu kryptograficznego w ramach programu Trusted Platform Module (TPM) lub PKCS # 11.</span><span class="sxs-lookup"><span data-stu-id="d8319-1387">For example, a hardware-based encryption engine may use a specific format not understood by the NetX Secure software, or a private key may be encrypted or represented by a cryptographic token as might be the case with a Trusted Platform Module (TPM) or PKCS#11 cryptographic hardware.</span></span> <span data-ttu-id="d8319-1388">Gdy używany jest typ klucza zdefiniowany przez użytkownika, dane klucza są przekazywane Verbatim do odpowiedniej procedury kryptograficznej — na przykład klucz prywatny RSA zostałby przekazana, bez analizy lub przetwarzania bezpośrednio do procedury kryptograficznej RSA dostarczonej do protokołu TLS w tabeli ciphersuite.</span><span class="sxs-lookup"><span data-stu-id="d8319-1388">When a user-defined key type is used, the key data is passed verbatim to the appropriate cryptographic routine - for example, an RSA private key would be passed, without any parsing or processing, directly to the RSA cryptographic routine provided to TLS in the ciphersuite table.</span></span> <span data-ttu-id="d8319-1389">Typ klucza zdefiniowany przez użytkownika jest również przekazywane do procedury kryptograficznej (w przypadku użycia algorytmu RSA jest to parametr "op").</span><span class="sxs-lookup"><span data-stu-id="d8319-1389">The user-defined key type is also passed to the cryptographic routine (in the case of RSA, this is the "op" parameter).</span></span>

<span data-ttu-id="d8319-1390">Zakres kluczy zdefiniowanych przez użytkownika obejmuje najwyższą połowę 32-bitowej nieoznaczonej liczby całkowitej z 0x0001 0000-0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="d8319-1390">The range of user-defined keys covers the top half of a 32-bit unsigned integer, from 0x0001 0000-0xFFFF FFFF.</span></span> <span data-ttu-id="d8319-1391">Wartości mniejsze niż 0x0001 0000 są zarezerwowane do bezpiecznego użycia NetX.</span><span class="sxs-lookup"><span data-stu-id="d8319-1391">Values less than 0x0001 0000 are reserved for NetX Secure use.</span></span>

<span data-ttu-id="d8319-1392">Typy kluczy zdefiniowane przez użytkownika to zaawansowana funkcja, która wymaga użycia niestandardowych procedur kryptograficznych do obsługi danych pierwotnego klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-1392">User-defined key types are an advanced feature that requires custom cryptographic routines to handle the raw private key data.</span></span> <span data-ttu-id="d8319-1393">Jeśli potrzebujesz tej funkcji, skontaktuj się z przedstawicielem logiki Express.</span><span class="sxs-lookup"><span data-stu-id="d8319-1393">Please contact your Express Logic representative if you have need of this feature.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1394">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1394">Parameters</span></span>

- <span data-ttu-id="d8319-1395">**certificate_ptr** Wskaźnik do niezainicjowanego wystąpienia certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="d8319-1395">**certificate_ptr** Pointer to an uninitialized X.509 Certificate instance.</span></span>
- <span data-ttu-id="d8319-1396">**certificate_data** Wskaźnik do danych binarnych X. 509 zakodowanych algorytmem DER.</span><span class="sxs-lookup"><span data-stu-id="d8319-1396">**certificate_data** Pointer to DER-encoded X.509 binary data.</span></span>
- <span data-ttu-id="d8319-1397">**raw_data_buffer** Wskaźnik na opcjonalny dedykowany bufor danych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d8319-1397">**raw_data_buffer** Pointer to optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="d8319-1398">**buffer_size** Rozmiar opcjonalnego dedykowanego buforu danych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d8319-1398">**buffer_size** Size of optional dedicated certificate data buffer.</span></span>
- <span data-ttu-id="d8319-1399">**certificate_data_length** Długość danych binarnych certyfikatu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="d8319-1399">**certificate_data_length** Length of certificate binary data in bytes.</span></span>
- <span data-ttu-id="d8319-1400">**private_key_data** Wskaźnik na opcjonalne dane klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-1400">**private_key_data** Pointer to optional private key data.</span></span>
- <span data-ttu-id="d8319-1401">**private_key_data_length** Długość danych klucza prywatnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-1401">**private_key_data_length** Length of private key data.</span></span>
- <span data-ttu-id="d8319-1402">**private_key_type** Identyfikator typu klucza.</span><span class="sxs-lookup"><span data-stu-id="d8319-1402">**private_key_type** Key type identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1403">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1403">Return Values</span></span>

- <span data-ttu-id="d8319-1404">**NX_SUCCESS** (0X00) pomyślne dodanie certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-1404">**NX_SUCCESS** (0x00) Successful addition of certificate.</span></span>
- <span data-ttu-id="d8319-1405">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d8319-1405">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>
- <span data-ttu-id="d8319-1406">Dane certyfikatu X. 509 **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) nie zawierają ZAKODOWANego algorytmem DER.</span><span class="sxs-lookup"><span data-stu-id="d8319-1406">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) Certificate data did not contain a DER-encoded X.509 certificate.</span></span>
- <span data-ttu-id="d8319-1407">Certyfikat **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) nie ma szyfru klucza publicznego, który jest obsługiwany przez NetX Secure.</span><span class="sxs-lookup"><span data-stu-id="d8319-1407">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) Certificate did not have a public-key cipher that is supported by NetX Secure.</span></span>
- <span data-ttu-id="d8319-1408">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) klucz prywatny lub certyfikat nie zawiera prawidłowej sekwencji ASN. 1.</span><span class="sxs-lookup"><span data-stu-id="d8319-1408">**NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** (0x186) Private key or certificate did not contain a valid ASN.1 sequence.</span></span>
- <span data-ttu-id="d8319-1409">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) podany klucz prywatny nie jest prawidłowym kluczem RSA PKCS # 1.</span><span class="sxs-lookup"><span data-stu-id="d8319-1409">**NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** (0x18A) The provided private key was not a valid PKCS#1 RSA key.</span></span>
- <span data-ttu-id="d8319-1410">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) podany typ klucza prywatnego nie został zdefiniowany przez użytkownika i nie jest zgodny z żadnym znanym typem.</span><span class="sxs-lookup"><span data-stu-id="d8319-1410">**NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** (0x19D) The private key type provided was not user-defined and did not match any known type.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1411">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1411">Allowed From</span></span>

<span data-ttu-id="d8319-1412">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1413">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1413">Example</span></span>

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a><span data-ttu-id="d8319-1414">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1414">See Also</span></span>

- <span data-ttu-id="d8319-1415">nx_secure_local_certificate_add</span><span class="sxs-lookup"><span data-stu-id="d8319-1415">nx_secure_local_certificate_add</span></span>
- <span data-ttu-id="d8319-1416">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-1416">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-1417">nx_secure_tls_remote_certificate_allocate</span><span class="sxs-lookup"><span data-stu-id="d8319-1417">nx_secure_tls_remote_certificate_allocate</span></span>
- <span data-ttu-id="d8319-1418">Importowanie certyfikatów X. 509 do NetX Secure w rozdziale 3.</span><span class="sxs-lookup"><span data-stu-id="d8319-1418">Importing X.509 Certificates into NetX Secure in Chapter 3.</span></span>

## <a name="nx_secure_x509_common_name_dns_check"></a><span data-ttu-id="d8319-1419">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="d8319-1419">nx_secure_x509_common_name_dns_check</span></span>

<span data-ttu-id="d8319-1420">Sprawdź nazwę DNS w odniesieniu do certyfikatu X. 509</span><span class="sxs-lookup"><span data-stu-id="d8319-1420">Check DNS name against X.509 Certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1421">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1421">Prototype</span></span>

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a><span data-ttu-id="d8319-1422">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1422">Description</span></span>

<span data-ttu-id="d8319-1423">Ta usługa sprawdza nazwę pospolitą certyfikatu względem nazwy domeny najwyższego poziomu (TLD) dostarczonej przez obiekt wywołujący do celów weryfikacji DNS hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="d8319-1423">This service checks a certificate's Common Name against a Top- Domain name (TLD) provided by the caller for the purposes of DNS validation of a remote host.</span></span> <span data-ttu-id="d8319-1424">Ta funkcja narzędziowa jest przeznaczona do wywoływania z poziomu procedury wywołania zwrotnego weryfikacji certyfikatu dostarczonej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="d8319-1424">This utility function is intended to be called from within a certificate validation callback routine provided by the application.</span></span> <span data-ttu-id="d8319-1425">Nazwa TLD powinna być górną częścią adresu URL służącego do uzyskiwania dostępu do hosta zdalnego ("." -rozdzielany ciąg przed pierwszym ukośnikiem).</span><span class="sxs-lookup"><span data-stu-id="d8319-1425">The TLD name should be the top part of the URL used to access the remote host (the "."-separated string before the first slash).</span></span> <span data-ttu-id="d8319-1426">Jeśli nazwa pospolita zawiera symbol wieloznaczny (na przykład *. example.com), symbol wieloznaczny będzie pasował do dowolnego sufiksu. Należy zauważyć, że tylko pierwszy symbol wieloznaczny ("*") (odczytywanie od prawej do lewej) będzie brany pod uwagę dla dopasowania symboli wieloznacznych — na przykład ABC. \*. przykład. com *będzie pasować do* nazwy kończącej się znakiem ". example.com".</span><span class="sxs-lookup"><span data-stu-id="d8319-1426">If the Common Name contains a wildcard (such as *.example.com), the wildcard will match any with the same suffix. Note that only the first wildcard ("*") encountered (reading right-to-left) will be considered for wildcard matching – for example, abc.\*.example.com will match *any* name ending in ".example.com".</span></span>

<span data-ttu-id="d8319-1427">Jeśli nazwa pospolita nie pasuje do podanego ciągu, rozszerzenie "subjectAltName" jest analizowane (jeśli istnieje w certyfikacie) i wszystkie wpisy DNSName są również porównywane.</span><span class="sxs-lookup"><span data-stu-id="d8319-1427">If the Common Name does not match the provided string, the "subjectAltName" extension is parsed (if it exists in the certificate) and any DNSName entries are also compared.</span></span> <span data-ttu-id="d8319-1428">Jeśli żadna z tych wpisów nie jest zgodna, zwracany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="d8319-1428">If none of those entries match, an error is returned.</span></span>

<span data-ttu-id="d8319-1429">Ważne jest, aby zrozumieć format nazwy pospolitej (i wpisów subjectAltName) w oczekiwanych certyfikatach.</span><span class="sxs-lookup"><span data-stu-id="d8319-1429">It is important to understand the format of the common name (and subjectAltName entries) in expected certificates.</span></span> <span data-ttu-id="d8319-1430">Na przykład niektóre certyfikaty mogą korzystać z surowego adresu IP lub symbolu wieloznacznego.</span><span class="sxs-lookup"><span data-stu-id="d8319-1430">For example, some certificates may use a raw IP address or a wild card.</span></span> <span data-ttu-id="d8319-1431">Ciąg TLD DNS musi być sformatowany w taki sposób, aby pasował do oczekiwanych wartości w odebranych certyfikatach.</span><span class="sxs-lookup"><span data-stu-id="d8319-1431">The DNS TLD string must be formatted such that it will match the expected values in received certificates.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1432">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1432">Parameters</span></span>

- <span data-ttu-id="d8319-1433">**certificate_ptr** Wskaźnik na wystąpienie certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="d8319-1433">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>
- <span data-ttu-id="d8319-1434">**dns_tld** Top-Level nazwy domeny do porównania.</span><span class="sxs-lookup"><span data-stu-id="d8319-1434">**dns_tld** Top-Level Domain name to compare against.</span></span>
- <span data-ttu-id="d8319-1435">**dns_tld_length** Długość ciągu TLD.</span><span class="sxs-lookup"><span data-stu-id="d8319-1435">**dns_tld_length** Length of TLD string.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1436">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1436">Return Values</span></span>

- <span data-ttu-id="d8319-1437">Pomyślne porównanie **NX_SUCCESS** (0x00) z nazwą pospolitą lub SubjectAltName.</span><span class="sxs-lookup"><span data-stu-id="d8319-1437">**NX_SUCCESS** (0x00) Successful comparison with Common Name or subjectAltName.</span></span>
- <span data-ttu-id="d8319-1438">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0X195) nie znaleziono zgodnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="d8319-1438">**NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** (0x195) No matching name found.</span></span>
- <span data-ttu-id="d8319-1439">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d8319-1439">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1440">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1440">Allowed From</span></span>

<span data-ttu-id="d8319-1441">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1441">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1442">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1442">Example</span></span>

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
UCHAR *tld = “www.example.com”;

    /* Check our DNS TLD against the certificate provided by the
       remote TLS host. */
    status = nx_secure_x509_common_name_dns_check(certificate, tld, strlen(tld));

        if(status != NX_SUCCESS)
        {
            /* TLD did not match any names in the certificate. */
            return(status);
        }

        /* DNS validation and any other checks were successful. */
        return(NX_SUCCESS);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="d8319-1443">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1443">See Also</span></span>

- <span data-ttu-id="d8319-1444">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-1444">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-1445">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1445">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="d8319-1446">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="d8319-1446">nx_secure_x509_crl_revocation_check</span></span>

## <a name="nx_secure_x509_crl_revocation_check"></a><span data-ttu-id="d8319-1447">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="d8319-1447">nx_secure_x509_crl_revocation_check</span></span>

<span data-ttu-id="d8319-1448">Sprawdź certyfikat X. 509 na podanej liście odwołania certyfikatów (CRL)</span><span class="sxs-lookup"><span data-stu-id="d8319-1448">Check X.509 Certificate against a supplied Certificate Revocation List (CRL)</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1449">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1449">Prototype</span></span>

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a><span data-ttu-id="d8319-1450">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1450">Description</span></span>

<span data-ttu-id="d8319-1451">Ta usługa przyjmuje listę odwołania certyfikatów zakodowaną algorytmem DER i wyszukuje określony certyfikat na tej liście.</span><span class="sxs-lookup"><span data-stu-id="d8319-1451">This service takes a DER-encoded Certificate Revocation List and searches for a specific certificate in that list.</span></span> <span data-ttu-id="d8319-1452">Wystawca listy CRL jest weryfikowany w odniesieniu do podanego magazynu certyfikatów, wystawca listy CRL jest zweryfikowany jako taki sam, jak w przypadku sprawdzanego certyfikatu i numer seryjny certyfikatu jest używany do przeszukiwania listy odwołanych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="d8319-1452">The issuer of the CRL is validated against a supplied certificate store, the CRL issuer is validated to be the same as the one for the certificate being checked, and the serial number of the certificate in question is used to search the revoked certificates list.</span></span> <span data-ttu-id="d8319-1453">Jeśli wystawcy są zgodni, podpis wyewidencjonowany i certyfikat **nie** znajduje się na liście, wywołanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d8319-1453">If the issuers match, the signature checks out, and the certificate is **not** present in the list, the call is successful.</span></span> <span data-ttu-id="d8319-1454">Wszystkie inne przypadki powodują zwrócenie błędu.</span><span class="sxs-lookup"><span data-stu-id="d8319-1454">All other cases cause an error to be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1455">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1455">Parameters</span></span>

- <span data-ttu-id="d8319-1456">**crl_data** Wskaźnik do listy CRL kodowanej algorytmem DER.</span><span class="sxs-lookup"><span data-stu-id="d8319-1456">**crl_data** Pointer to a DER-encoded CRL.</span></span>
- <span data-ttu-id="d8319-1457">**crl_length** Długość w bajtach danych listy CRL.</span><span class="sxs-lookup"><span data-stu-id="d8319-1457">**crl_length** Length in bytes of CRL data.</span></span>
- <span data-ttu-id="d8319-1458">**Magazyn** Wskaźnik do magazynu certyfikatów X. 509.</span><span class="sxs-lookup"><span data-stu-id="d8319-1458">**store** Pointer to an X.509 Certificate store.</span></span>
- <span data-ttu-id="d8319-1459">**certificate_ptr** Wskaźnik na wystąpienie certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="d8319-1459">**certificate_ptr** Pointer to an X.509 Certificate instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1460">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1460">Return Values</span></span>

- <span data-ttu-id="d8319-1461">**NX_SUCCESS** (0x00) — pomyślne sprawdzenie poprawności certyfikatu nie zostało odwołane.</span><span class="sxs-lookup"><span data-stu-id="d8319-1461">**NX_SUCCESS** (0x00) Successful validation that the certificate was not revoked.</span></span>
- <span data-ttu-id="d8319-1462">Nie znaleziono certyfikatu wystawcy listy CRL **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119).</span><span class="sxs-lookup"><span data-stu-id="d8319-1462">**NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) CRL issuer certificate not found.</span></span>
- <span data-ttu-id="d8319-1463">Nie znaleziono certyfikatu wystawcy certyfikatu **NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B).</span><span class="sxs-lookup"><span data-stu-id="d8319-1463">**NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** 0x11B) Certificate issuer certificate not found.</span></span>
- <span data-ttu-id="d8319-1464">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) numer ASN listy CRL. 1 zawiera pole nieprawidłowej długości.</span><span class="sxs-lookup"><span data-stu-id="d8319-1464">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) The CRL ASN.1 contained an invalid length field.</span></span>
- <span data-ttu-id="d8319-1465">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG (0x189)** Lista CRL zawiera nieprawidłowy numer ASN. 1.</span><span class="sxs-lookup"><span data-stu-id="d8319-1465">**NX_SECURE_X509_UNEXPECTED_ASN1_TAG(0x189)** The CRL contained invalid ASN.1.</span></span>
- <span data-ttu-id="d8319-1466">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18c) weryfikacja łańcucha certyfikatów nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="d8319-1466">**NX_SECURE_X509_CHAIN_VERIFY_FAILURE** (0x18C) A certificate chain verification failed.</span></span>
- <span data-ttu-id="d8319-1467">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0X197) lista CRL i wystawcy certyfikatów nie są zgodne.</span><span class="sxs-lookup"><span data-stu-id="d8319-1467">**NX_SECURE_X509_CRL_ISSUER_MISMATCH** (0x197) CRL and certificate issuers did not match.</span></span>
- <span data-ttu-id="d8319-1468">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) podpis listy CRL był nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d8319-1468">**NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** 0x198) The CRL signature was invalid.</span></span>
- <span data-ttu-id="d8319-1469">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) sprawdzany certyfikat został znaleziony w liście CRL i dlatego jest odwołany.</span><span class="sxs-lookup"><span data-stu-id="d8319-1469">**NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** (0x199) The certificate being checked was found in the CRL and is therefore revoked.</span></span>
- <span data-ttu-id="d8319-1470">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d8319-1470">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1471">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1471">Allowed From</span></span>

<span data-ttu-id="d8319-1472">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1472">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1473">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1473">Example</span></span>

```C
/* CRL obtained for the expected certificate issuer through some means (downloaded
   from server manually, obtained from CRL endpoint, etc…) */
const UCHAR *crl_data;
UINT crl_length = 300;

/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
NX_SECURE_X509_CERTIFICATE_STORE *store;

    /* Obtain a certificate store to check against. In the certificate callback,
       it usually makes the most sense to use the store associated with the TLS
       session. */
    store = &session -> nx_secure_tls_credentials.nx_secure_tls_certificate_store;

    /* Check our certificate against the CRL and TLS certificate store. */
    status = nx_secure_x509_crl_revocation_check(crl, crl_length, store,
                                                 certificate);

        if(status != NX_SUCCESS)
        {
            if(status == NX_SECURE_X509_CRL_CERTIFICATE_REVOKED)
            {
                /* Certificate was revoked. */
               return(status);
            }
            else
            {
               /* CRL was invalid or some other issue. In this case the certificate
                  may still be valid since the CRL itself was a problem. At this
                  point it is up to the application to decide whether to continue
                  with the TLS handshake. For this example, assume certificate is
                  valid (faulty CRL is a possible Denial-of-Service attack).*/
               status = NX_SUCCESS;
        }

    /* Other certificate checking can go here. */

    /* Return status of certificate checks. */
    return(status);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a><span data-ttu-id="d8319-1474">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1474">See Also</span></span>

- <span data-ttu-id="d8319-1475">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-1475">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-1476">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1476">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="d8319-1477">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="d8319-1477">nx_secure_x509_common_name_dns_check</span></span>

## <a name="nx_secure_x509_dns_name_initialize"></a><span data-ttu-id="d8319-1478">nx_secure_x509_dns_name_initialize</span><span class="sxs-lookup"><span data-stu-id="d8319-1478">nx_secure_x509_dns_name_initialize</span></span>

<span data-ttu-id="d8319-1479">Zainicjuj strukturę nazw DNS X. 509</span><span class="sxs-lookup"><span data-stu-id="d8319-1479">Initialize an X.509 DNS name structure</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1480">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1480">Prototype</span></span>

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a><span data-ttu-id="d8319-1481">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1481">Description</span></span>

<span data-ttu-id="d8319-1482">Ta usługa inicjuje nazwę DNS X. 509 do użycia z niektórymi usługami interfejsu API wymagającymi określonego formatu nazwy.</span><span class="sxs-lookup"><span data-stu-id="d8319-1482">This service initializes an X.509 DNS name for use with certain API services requiring a specific name format.</span></span> <span data-ttu-id="d8319-1483">Na przykład usługa *nx_secure_tls_sni_extension_parse* oczekuje obiektu NX_SECURE_X509_DNS_NAME w celu dopasowania nazwy dostarczonej przez hosta zdalnego w rozszerzeniu oznaczanie nazwy serwera podczas UZGADNIANIA protokołu TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1483">For example, the *nx_secure_tls_sni_extension_parse* service expects an NX_SECURE_X509_DNS_NAME object in order to match the name provided by a remote host in the Server Name Indication extension during the TLS handshake.</span></span> <span data-ttu-id="d8319-1484">Nazwa DNS jest po prostu ciągiem charater o długości — Maksymalna dozwolona długość nazwy DNS (i rozmiar buforu wewnętrznego w NX_SECURE_X509_DNS_NAME) jest kontrolowana przez NX_SECURE_X509_DNS_NAME_MAX makro (domyślnie 100 bajtów).</span><span class="sxs-lookup"><span data-stu-id="d8319-1484">A DNS name is simply a charater string with a length – the maximum allowed length of a DNS name (and the size of the internal buffer in NX_SECURE_X509_DNS_NAME) is controlled by the macro NX_SECURE_X509_DNS_NAME_MAX (default 100 bytes).</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1485">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1485">Parameters</span></span>

- <span data-ttu-id="d8319-1486">**dns_name** Struktura nazw DNS do zainicjowania.</span><span class="sxs-lookup"><span data-stu-id="d8319-1486">**dns_name** DNS name structure to initialize.</span></span>
- <span data-ttu-id="d8319-1487">**name_string** Dane ciągu nazwy DNS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1487">**name_string** DNS name string data.</span></span>
- <span data-ttu-id="d8319-1488">**Długość** Długość ciągu nazwy.</span><span class="sxs-lookup"><span data-stu-id="d8319-1488">**length** Length of name string.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1489">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1489">Return Values</span></span>

- <span data-ttu-id="d8319-1490">Pomyślnie zainicjowano **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="d8319-1490">**NX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="d8319-1491">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) określony ciąg nazwy został przekroczony NX_SECURE_X509_DNS_NAME_MAX.</span><span class="sxs-lookup"><span data-stu-id="d8319-1491">**NX_SECURE_X509_NAME_STRING_TOO_LONG** (0x19E) The given name string exceeded NX_SECURE_X509_DNS_NAME_MAX.</span></span>
- <span data-ttu-id="d8319-1492">**NX_PTR_ERROR** (0X07) próbował użyć nieprawidłowego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d8319-1492">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1493">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1493">Allowed From</span></span>

<span data-ttu-id="d8319-1494">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1494">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1495">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1495">Example</span></span>

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a><span data-ttu-id="d8319-1496">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1496">See Also</span></span>

- <span data-ttu-id="d8319-1497">nx_secure_tls_session_create</span><span class="sxs-lookup"><span data-stu-id="d8319-1497">nx_secure_tls_session_create</span></span>
- <span data-ttu-id="d8319-1498">nx_secure_tls_session_sni_extension_parse</span><span class="sxs-lookup"><span data-stu-id="d8319-1498">nx_secure_tls_session_sni_extension_parse</span></span>
- <span data-ttu-id="d8319-1499">nx_secure_tls_session_sni_extension_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1499">nx_secure_tls_session_sni_extension_set</span></span>

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a><span data-ttu-id="d8319-1500">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="d8319-1500">nx_secure_x509_extended_key_usage_extension_parse</span></span>

<span data-ttu-id="d8319-1501">Znajdowanie i analizowanie rozszerzenia rozszerzonego użycia klucza X. 509 w certyfikacie X. 509</span><span class="sxs-lookup"><span data-stu-id="d8319-1501">Find and parse an X.509 extended key usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1502">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1502">Prototype</span></span>

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a><span data-ttu-id="d8319-1503">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1503">Description</span></span>

<span data-ttu-id="d8319-1504">Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego weryfikacji certyfikatu (zobacz *nx_secure_tls_session_certificate_callback_set)*.</span><span class="sxs-lookup"><span data-stu-id="d8319-1504">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="d8319-1505">Wyszuka określony identyfikator OID rozszerzonego użycia klucza w ramach certyfikatu X. 509 i zwróci, czy identyfikator OID jest obecny.</span><span class="sxs-lookup"><span data-stu-id="d8319-1505">It will search for a specific extended key usage OID within an X.509 certificate and return whether the OID is present.</span></span> <span data-ttu-id="d8319-1506">Key_usage parametr to liczba całkowita mapowania identyfikatorów OID, które są używane wewnętrznie przez NetX Secure X. 509 i TLS, aby uniknąć przekazywania ciągów identyfikatorów OID o zmiennej długości jako parametrów.</span><span class="sxs-lookup"><span data-stu-id="d8319-1506">The key_usage parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="d8319-1507">Odpowiednie identyfikatory OID rozszerzenia rozszerzonego użycia klucza podano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d8319-1507">The relevant OIDs for the extended key usage extension are given in the table below.</span></span> <span data-ttu-id="d8319-1508">Typowa implementacja klienta TLS, która chce sprawdzić użycie klucza rozszerzonego w otrzymanym certyfikacie serwera TLS, sprawdza obecność identyfikatora OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH — Jeśli rozszerzenie jest obecne, ale nie ma tego identyfikatora OID, certyfikat będzie uznawany za nieprawidłowy dla identyfikowanie hosta jako serwer TLS, a wywołanie zwrotne weryfikacji certyfikatu powinno zwrócić błąd.</span><span class="sxs-lookup"><span data-stu-id="d8319-1508">A typical TLS Client implementation wishing to check extended key usage in a received TLS server certificate would check for the existence of the OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH – if the extension is present but that OID is not, then the certificate would be considered invalid for identifiying the host as a TLS server and the certificate verification callback should return an error.</span></span> <span data-ttu-id="d8319-1509">Jeśli rozszerzenie nie istnieje, wówczas jest do aplikacji, niezależnie od tego, czy należy kontynuować uzgadnianie TLS.</span><span class="sxs-lookup"><span data-stu-id="d8319-1509">If the extension itself is missing, then it is up to the application whether or not to proceed with the TLS handshake.</span></span>

<span data-ttu-id="d8319-1510">W wywołaniu zwrotnym weryfikacji certyfikatu Kod powrotu błędu NX_SECURE_X509_KEY_USAGE_ERROR jest zarezerwowany do użytku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8319-1510">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="d8319-1511">Jeśli wystąpi błąd podczas sprawdzania użycia klucza, ta wartość może zostać zwrócona z wywołania zwrotnego, aby wskazać przyczynę niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="d8319-1511">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="d8319-1512">Bezpieczny identyfikator NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-1512">NetX Secure Identifier</span></span>                                | <span data-ttu-id="d8319-1513">Wartość identyfikatora OID</span><span class="sxs-lookup"><span data-stu-id="d8319-1513">OID Value</span></span>         | <span data-ttu-id="d8319-1514">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1514">Description</span></span>                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| <span data-ttu-id="d8319-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span><span class="sxs-lookup"><span data-stu-id="d8319-1515">NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH</span></span>   | <span data-ttu-id="d8319-1516">1.3.6.1.5.5.7.3.1</span><span class="sxs-lookup"><span data-stu-id="d8319-1516">1.3.6.1.5.5.7.3.1</span></span> | <span data-ttu-id="d8319-1517">Certyfikat może służyć do identyfikowania serwera TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-1517">Certificate can be used to identify a TLS server</span></span> |
| <span data-ttu-id="d8319-1518">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span><span class="sxs-lookup"><span data-stu-id="d8319-1518">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH</span></span>   | <span data-ttu-id="d8319-1519">1.3.6.1.5.5.7.3.2</span><span class="sxs-lookup"><span data-stu-id="d8319-1519">1.3.6.1.5.5.7.3.2</span></span> | <span data-ttu-id="d8319-1520">Certyfikat może służyć do identyfikowania klienta TLS</span><span class="sxs-lookup"><span data-stu-id="d8319-1520">Certificate can be used to identify a TLS client</span></span> |
| <span data-ttu-id="d8319-1521">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span><span class="sxs-lookup"><span data-stu-id="d8319-1521">NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING</span></span>  | <span data-ttu-id="d8319-1522">1.3.6.1.5.5.7.3.3</span><span class="sxs-lookup"><span data-stu-id="d8319-1522">1.3.6.1.5.5.7.3.3</span></span> | <span data-ttu-id="d8319-1523">Certyfikat może służyć do podpisywania kodu</span><span class="sxs-lookup"><span data-stu-id="d8319-1523">Certificate can be used to sign code</span></span>             |
| <span data-ttu-id="d8319-1524">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span><span class="sxs-lookup"><span data-stu-id="d8319-1524">NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT</span></span> | <span data-ttu-id="d8319-1525">1.3.6.1.5.5.7.3.4</span><span class="sxs-lookup"><span data-stu-id="d8319-1525">1.3.6.1.5.5.7.3.4</span></span> | <span data-ttu-id="d8319-1526">Certyfikat może służyć do podpisywania wiadomości e-mail</span><span class="sxs-lookup"><span data-stu-id="d8319-1526">Certificate can be used to sign emails</span></span>           |
| <span data-ttu-id="d8319-1527">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span><span class="sxs-lookup"><span data-stu-id="d8319-1527">NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING</span></span> | <span data-ttu-id="d8319-1528">1.3.6.1.5.5.7.3.8</span><span class="sxs-lookup"><span data-stu-id="d8319-1528">1.3.6.1.5.5.7.3.8</span></span> | <span data-ttu-id="d8319-1529">Certyfikat może służyć do podpisywania znaczników czasu</span><span class="sxs-lookup"><span data-stu-id="d8319-1529">Certificate can be used to sign timestamps</span></span>       |
| <span data-ttu-id="d8319-1530">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span><span class="sxs-lookup"><span data-stu-id="d8319-1530">NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING</span></span>  | <span data-ttu-id="d8319-1531">1.3.6.1.5.5.7.3.9</span><span class="sxs-lookup"><span data-stu-id="d8319-1531">1.3.6.1.5.5.7.3.9</span></span> | <span data-ttu-id="d8319-1532">Certyfikat może służyć do podpisywania odpowiedzi protokołu OCSP</span><span class="sxs-lookup"><span data-stu-id="d8319-1532">Certificate can be used to sign OCSP responses</span></span>   |

<span data-ttu-id="d8319-1533">Identyfikatory OID i mapowania dla rozszerzenia rozszerzonego użycia klucza X. 509</span><span class="sxs-lookup"><span data-stu-id="d8319-1533">OIDs and mappings for X.509 Extended Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1534">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1534">Parameters</span></span>

- <span data-ttu-id="d8319-1535">**certyfikat** Wskaźnik do zweryfikowanego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-1535">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="d8319-1536">**KEY_USAGE** Mapowanie wartości całkowitej OID z tabeli powyżej.</span><span class="sxs-lookup"><span data-stu-id="d8319-1536">**key_usage** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1537">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1537">Return Values</span></span>

- <span data-ttu-id="d8319-1538">**NX_SUCCESS** (0x00) znaleziono identyfikator OID użycia klucza.</span><span class="sxs-lookup"><span data-stu-id="d8319-1538">**NX_SUCCESS** (0x00) Specified key usage OID found.</span></span>
- <span data-ttu-id="d8319-1539">Napotkano **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0X181) ASN. 1 tag wielobajtowy (nieobsługiwany certyfikat).</span><span class="sxs-lookup"><span data-stu-id="d8319-1539">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="d8319-1540">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) niedozwolone pole ASN. 1 (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="d8319-1540">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="d8319-1541">**NX_SECURE_X509_INVALID_TAG_CLASS** (0X190) Nieprawidłowa Klasa tagu ASN. 1 (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="d8319-1541">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="d8319-1542">Napotkano nieprawidłowe rozszerzenie **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="d8319-1542">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="d8319-1543">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) rozszerzenie rozszerzonego użycia klucza nie zostało znalezione w podanym certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="d8319-1543">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The Extended Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="d8319-1544">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-1544">**NX_PTR_ERROR** (0x07) Invalid certificate pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1545">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1545">Allowed From</span></span>

<span data-ttu-id="d8319-1546">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1546">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1547">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1547">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT* certificate)
{
UINT status;

    /* Extended key usage - look for specific OIDs. */
    status = nx_secure_x509_extended_key_usage_extension_parse(certificate,
                        NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH);

    if(status != NX_SUCCESS)
    {
        if(NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND)
        {
            printf("Extended key usage extension not found or specified key usage OID not
                    provided in extension.\n");
            /* The certificate was valid but the specified OID was not found. The
               application can decide whether to continue or abort the TLS handshake. */
            return(NX_SECURE_X509_KEY_USAGE_ERROR);
        }
        else
        {
            /* The extension or certificate was invalid. */
            return(status);
        }
    }

    /* The specified OID was found, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="d8319-1548">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1548">See Also</span></span>

- <span data-ttu-id="d8319-1549">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1549">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="d8319-1550">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="d8319-1550">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="d8319-1551">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="d8319-1551">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="d8319-1552">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="d8319-1552">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="d8319-1553">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="d8319-1553">nx_secure_x509_extension_find</span></span>

## <a name="nx_secure_x509_extension_find"></a><span data-ttu-id="d8319-1554">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="d8319-1554">nx_secure_x509_extension_find</span></span>

<span data-ttu-id="d8319-1555">Znajdź i zwróć rozszerzenie X. 509 w certyfikacie X. 509</span><span class="sxs-lookup"><span data-stu-id="d8319-1555">Find and return an X.509 extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1556">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1556">Prototype</span></span>

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a><span data-ttu-id="d8319-1557">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1557">Description</span></span>

<span data-ttu-id="d8319-1558">Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego weryfikacji certyfikatu (zobacz *nx_secure_tls_session_certificate_callback_set)* i jest zaawansowaną usługą X. 509.</span><span class="sxs-lookup"><span data-stu-id="d8319-1558">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)* and is an advanced X.509 service.</span></span>

<span data-ttu-id="d8319-1559">Funkcja będzie wyszukiwać określone rozszerzenie w ramach certyfikatu X. 509 na podstawie identyfikatora OID i zwracać, czy identyfikator OID jest obecny, wraz ze strukturą zawierającą odwołania do odpowiednich nieprzetworzonych danych rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d8319-1559">The function will search for a specific extension within an X.509 certificate based on an OID and return whether the OID is present, along with a structure containing references to the relevant raw extension data.</span></span> <span data-ttu-id="d8319-1560">Extension_id parametr to liczba całkowita mapowania identyfikatorów OID, które są używane wewnętrznie przez NetX Secure X. 509 i TLS, aby uniknąć przekazywania ciągów identyfikatorów OID o zmiennej długości jako parametrów.</span><span class="sxs-lookup"><span data-stu-id="d8319-1560">The extension_id parameter is an integer mapping of the OIDs which is used internally by NetX Secure X.509 and TLS to avoid passing the variable-length OID strings as parameters.</span></span>

<span data-ttu-id="d8319-1561">Funkcje pomocnika zapewniane dla określonych rozszerzeń (takich jak *nx_secure_x509_key_usage_extension_parse*) nx_secure_x509_extension_find wewnętrznie w celu uzyskania danych rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d8319-1561">The helper functions provided for specific extensions (such as *nx_secure_x509_key_usage_extension_parse*) call nx_secure_x509_extension_find internally to obtain the extension data.</span></span>

<span data-ttu-id="d8319-1562">Odpowiednie identyfikatory OID dla znanych rozszerzeń X. 509 podano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d8319-1562">The relevant OIDs for known X.509 extensions are given in the table below.</span></span>

<span data-ttu-id="d8319-1563">Struktura NX_SECURE_X509_EXTENSION zawiera wskaźniki do certyfikatu X. 509, które zezwalają na funkcje pomocnika, takie jak *nx_secure_x509_key_usage_extension_parse* , aby szybko zdekodować dane ASN. 1 ZAKODOWANe algorytmem DER.</span><span class="sxs-lookup"><span data-stu-id="d8319-1563">The NX_SECURE_X509_EXTENSION structure contains pointers into the X.509 certificate that allow helper functions such as *nx_secure_x509_key_usage_extension_parse* to quickly decode the raw extension DER-encoded ASN.1 data.</span></span>

<span data-ttu-id="d8319-1564">Aby uzyskać informacje o określonych rozszerzeniach, zobacz RFC 5280 (Specyfikacja X. 509) lub odwołanie do odpowiednich funkcji pomocnika, jeśli są dostępne.</span><span class="sxs-lookup"><span data-stu-id="d8319-1564">For information on specific extensions, see RFC 5280 (X.509 specification) or the reference for the appropriate helper functions if available.</span></span>

<span data-ttu-id="d8319-1565">Bieżąca wersja NetX Secure X. 509 ma ograniczoną obsługę rozszerzeń X. 509.</span><span class="sxs-lookup"><span data-stu-id="d8319-1565">The current version of NetX Secure X.509 has limited support for X.509 extensions.</span></span> <span data-ttu-id="d8319-1566">W przyszłości zostaną dodane więcej funkcji pomocnika.</span><span class="sxs-lookup"><span data-stu-id="d8319-1566">More helper functions will be added in the future.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8319-1567">*Ta usługa jest zaawansowaną funkcją dla użytkowników zaznajomionych z rozszerzeniami X. 509 i numerem ASN szyfrowanym algorytmem DER. 1. Jest udostępniana, aby umożliwić tym użytkownikom dostęp do rozszerzeń, dla których NetX Secure X. 509 nie udostępnia obecnie funkcji pomocnika. W przypadku tych rozszerzeń bez funkcji pomocniczych należy samodzielnie przeanalizować pierwotny numer ASN szyfrowany algorytmem DER. 1.*</span><span class="sxs-lookup"><span data-stu-id="d8319-1567">*This service is an advanced feature for users familiar with X.509 extensions and DER-encoded ASN.1. It is provided to enable those users to access extensions for which NetX Secure X.509 does not currently provide helper functions. For those extensions without helper functions, you will have to parse the raw DER-encoded ASN.1 yourself.*</span></span>

| <span data-ttu-id="d8319-1568">Bezpieczny identyfikator NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-1568">NetX Secure Identifier</span></span>                              | <span data-ttu-id="d8319-1569">Wartość identyfikatora OID</span><span class="sxs-lookup"><span data-stu-id="d8319-1569">OID Value</span></span> | <span data-ttu-id="d8319-1570">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1570">Description</span></span>                                                                    | <span data-ttu-id="d8319-1571">Funkcja pomocnika?</span><span class="sxs-lookup"><span data-stu-id="d8319-1571">Helper function?</span></span> |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| <span data-ttu-id="d8319-1572">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span><span class="sxs-lookup"><span data-stu-id="d8319-1572">NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES</span></span>  | <span data-ttu-id="d8319-1573">2.5.29.9</span><span class="sxs-lookup"><span data-stu-id="d8319-1573">2.5.29.9</span></span>  | <span data-ttu-id="d8319-1574">Atrybuty katalogu — podstawowe atrybuty informacji o podmiotu certyfikatu</span><span class="sxs-lookup"><span data-stu-id="d8319-1574">Directory Attributes – basic information attributes about certificate subject</span></span>  | <span data-ttu-id="d8319-1575">Nie</span><span class="sxs-lookup"><span data-stu-id="d8319-1575">No</span></span>               |
| <span data-ttu-id="d8319-1576">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="d8319-1576">NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID</span></span>       | <span data-ttu-id="d8319-1577">2.5.29.14</span><span class="sxs-lookup"><span data-stu-id="d8319-1577">2.5.29.14</span></span> | <span data-ttu-id="d8319-1578">Służy do identyfikowania określonego klucza publicznego</span><span class="sxs-lookup"><span data-stu-id="d8319-1578">Used to identify a specific public key</span></span>                                         | <span data-ttu-id="d8319-1579">Nie</span><span class="sxs-lookup"><span data-stu-id="d8319-1579">No</span></span>               |
| <span data-ttu-id="d8319-1580">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="d8319-1580">NX_SECURE_TLS_X509_TYPE_KEY_USAGE</span></span>             | <span data-ttu-id="d8319-1581">2.5.29.15</span><span class="sxs-lookup"><span data-stu-id="d8319-1581">2.5.29.15</span></span> | <span data-ttu-id="d8319-1582">Zawiera informacje dotyczące prawidłowych użycia klucza publicznego certyfikatu</span><span class="sxs-lookup"><span data-stu-id="d8319-1582">Provides information on valid uses for the certificate public key</span></span>              | <span data-ttu-id="d8319-1583">Tak</span><span class="sxs-lookup"><span data-stu-id="d8319-1583">Yes</span></span>              |
| <span data-ttu-id="d8319-1584">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="d8319-1584">NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME</span></span>     | <span data-ttu-id="d8319-1585">2.5.29.17</span><span class="sxs-lookup"><span data-stu-id="d8319-1585">2.5.29.17</span></span> | <span data-ttu-id="d8319-1586">Zapewnia alternatywne nazwy DNS do identyfikacji certyfikatu</span><span class="sxs-lookup"><span data-stu-id="d8319-1586">Provides alternative DNS names to identify the certificate</span></span>                     | <span data-ttu-id="d8319-1587">Tak<sup>24</sup></span><span class="sxs-lookup"><span data-stu-id="d8319-1587">Yes<sup>24</sup></span></span>        |
| <span data-ttu-id="d8319-1588">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span><span class="sxs-lookup"><span data-stu-id="d8319-1588">NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME</span></span>      | <span data-ttu-id="d8319-1589">2.5.29.18</span><span class="sxs-lookup"><span data-stu-id="d8319-1589">2.5.29.18</span></span> | <span data-ttu-id="d8319-1590">Udostępnia alternatywne nazwy DNS w celu identyfikowania wystawcy certyfikatu</span><span class="sxs-lookup"><span data-stu-id="d8319-1590">Provides alternative DNS names to identify the certificate's issuer</span></span>            | <span data-ttu-id="d8319-1591">Nie</span><span class="sxs-lookup"><span data-stu-id="d8319-1591">No</span></span>               |
| <span data-ttu-id="d8319-1592">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="d8319-1592">NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS</span></span>     | <span data-ttu-id="d8319-1593">2.5.29.19</span><span class="sxs-lookup"><span data-stu-id="d8319-1593">2.5.29.19</span></span> | <span data-ttu-id="d8319-1594">Zawiera podstawowe informacje o ograniczeniach użycia certyfikatu</span><span class="sxs-lookup"><span data-stu-id="d8319-1594">Provides basic certificate usage constraint information</span></span>                        | <span data-ttu-id="d8319-1595">Nie</span><span class="sxs-lookup"><span data-stu-id="d8319-1595">No</span></span>               |
| <span data-ttu-id="d8319-1596">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="d8319-1596">NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS</span></span>      | <span data-ttu-id="d8319-1597">2.5.29.30</span><span class="sxs-lookup"><span data-stu-id="d8319-1597">2.5.29.30</span></span> | <span data-ttu-id="d8319-1598">Służy do ograniczania nazw certyfikatów do określonych domen</span><span class="sxs-lookup"><span data-stu-id="d8319-1598">Used to constrain certificate names to specific domains</span></span>                        | <span data-ttu-id="d8319-1599">Nie</span><span class="sxs-lookup"><span data-stu-id="d8319-1599">No</span></span>               |
| <span data-ttu-id="d8319-1600">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span><span class="sxs-lookup"><span data-stu-id="d8319-1600">NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION</span></span>      | <span data-ttu-id="d8319-1601">2.5.29.31</span><span class="sxs-lookup"><span data-stu-id="d8319-1601">2.5.29.31</span></span> | <span data-ttu-id="d8319-1602">Zawiera identyfikatory URI dystrybucji list CRL</span><span class="sxs-lookup"><span data-stu-id="d8319-1602">Provides URIs for CRL distribution</span></span>                                             | <span data-ttu-id="d8319-1603">Nie</span><span class="sxs-lookup"><span data-stu-id="d8319-1603">No</span></span>               |
| <span data-ttu-id="d8319-1604">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span><span class="sxs-lookup"><span data-stu-id="d8319-1604">NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES</span></span>  | <span data-ttu-id="d8319-1605">2.5.29.32</span><span class="sxs-lookup"><span data-stu-id="d8319-1605">2.5.29.32</span></span> | <span data-ttu-id="d8319-1606">Lista zasad certyfikatów dla dużych systemów infrastruktury kluczy publicznych</span><span class="sxs-lookup"><span data-stu-id="d8319-1606">List of certificate policies for large PKI systems</span></span>                             | <span data-ttu-id="d8319-1607">Nie</span><span class="sxs-lookup"><span data-stu-id="d8319-1607">No</span></span>               |
| <span data-ttu-id="d8319-1608">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span><span class="sxs-lookup"><span data-stu-id="d8319-1608">NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS</span></span> | <span data-ttu-id="d8319-1609">2.5.29.33</span><span class="sxs-lookup"><span data-stu-id="d8319-1609">2.5.29.33</span></span> | <span data-ttu-id="d8319-1610">Lista zasad certyfikatów urzędu certyfikacji</span><span class="sxs-lookup"><span data-stu-id="d8319-1610">List of CA certificate policies</span></span>                                                | <span data-ttu-id="d8319-1611">Nie</span><span class="sxs-lookup"><span data-stu-id="d8319-1611">No</span></span>               |
| <span data-ttu-id="d8319-1612">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span><span class="sxs-lookup"><span data-stu-id="d8319-1612">NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID</span></span>     | <span data-ttu-id="d8319-1613">2.5.29.35</span><span class="sxs-lookup"><span data-stu-id="d8319-1613">2.5.29.35</span></span> | <span data-ttu-id="d8319-1614">Służy do identyfikowania określonego klucza publicznego skojarzonego z podpisem certyfikatu</span><span class="sxs-lookup"><span data-stu-id="d8319-1614">Used to identify a specific public key associated with a certificate signature</span></span> | <span data-ttu-id="d8319-1615">Nie</span><span class="sxs-lookup"><span data-stu-id="d8319-1615">No</span></span>               |
| <span data-ttu-id="d8319-1616">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span><span class="sxs-lookup"><span data-stu-id="d8319-1616">NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS</span></span>    | <span data-ttu-id="d8319-1617">2.5.29.36</span><span class="sxs-lookup"><span data-stu-id="d8319-1617">2.5.29.36</span></span> | <span data-ttu-id="d8319-1618">Ograniczenia zasad urzędu certyfikacji</span><span class="sxs-lookup"><span data-stu-id="d8319-1618">CA policy constraints</span></span>                                                          | <span data-ttu-id="d8319-1619">Nie</span><span class="sxs-lookup"><span data-stu-id="d8319-1619">No</span></span>               |
| <span data-ttu-id="d8319-1620">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span><span class="sxs-lookup"><span data-stu-id="d8319-1620">NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE</span></span>   | <span data-ttu-id="d8319-1621">2.5.29.37</span><span class="sxs-lookup"><span data-stu-id="d8319-1621">2.5.29.37</span></span> | <span data-ttu-id="d8319-1622">Dodatkowe informacje o użyciu klucza opartego na identyfikatorze OID</span><span class="sxs-lookup"><span data-stu-id="d8319-1622">Additional OID-based key usage information</span></span>                                     | <span data-ttu-id="d8319-1623">Tak</span><span class="sxs-lookup"><span data-stu-id="d8319-1623">Yes</span></span>              |
| <span data-ttu-id="d8319-1624">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span><span class="sxs-lookup"><span data-stu-id="d8319-1624">NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL</span></span>          | <span data-ttu-id="d8319-1625">2.5.29.46</span><span class="sxs-lookup"><span data-stu-id="d8319-1625">2.5.29.46</span></span> | <span data-ttu-id="d8319-1626">Zawiera informacje dotyczące uzyskiwania różnicowych list CRL</span><span class="sxs-lookup"><span data-stu-id="d8319-1626">Provides information for obtaining delta CRLs</span></span>                                  | <span data-ttu-id="d8319-1627">Nie</span><span class="sxs-lookup"><span data-stu-id="d8319-1627">No</span></span>               |
| <span data-ttu-id="d8319-1628">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span><span class="sxs-lookup"><span data-stu-id="d8319-1628">NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY</span></span>     | <span data-ttu-id="d8319-1629">2.5.29.54</span><span class="sxs-lookup"><span data-stu-id="d8319-1629">2.5.29.54</span></span> | <span data-ttu-id="d8319-1630">Pole certyfikatu urzędu certyfikacji wskazujące, że nie można użyć AnyPolicy</span><span class="sxs-lookup"><span data-stu-id="d8319-1630">CA certificate field indicating that AnyPolicy cannot be used</span></span>                  | <span data-ttu-id="d8319-1631">Nie</span><span class="sxs-lookup"><span data-stu-id="d8319-1631">No</span></span>               |

<span data-ttu-id="d8319-1632">Identyfikatory OID i mapowania dla rozszerzeń X. 509</span><span class="sxs-lookup"><span data-stu-id="d8319-1632">OIDs and mappings for X.509 Extensions</span></span>

24. <span data-ttu-id="d8319-1633">Rozszerzenie SubjectAltName jest analizowane w ramach sprawdzania nazw DNS w usłudze nx_secure_x509_common_name_dns_check.</span><span class="sxs-lookup"><span data-stu-id="d8319-1633">The SubjectAltName extension is parsed as part of the DNS name check in the service nx_secure_x509_common_name_dns_check.</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1634">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1634">Parameters</span></span>

- <span data-ttu-id="d8319-1635">**certyfikat** Wskaźnik do zweryfikowanego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-1635">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="d8319-1636">**rozszerzenie** Zwróć strukturę zawierającą wskaźnik i długość danych rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d8319-1636">**extension** Return structure containing extension data pointer and length.</span></span>
- <span data-ttu-id="d8319-1637">**extension_id** Mapowanie wartości całkowitej OID z tabeli powyżej.</span><span class="sxs-lookup"><span data-stu-id="d8319-1637">**extension_id** OID integer mapping from table above.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1638">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1638">Return Values</span></span>

- <span data-ttu-id="d8319-1639">Znaleziono identyfikator OID określonego rozszerzenia **NX_SUCCESS** (0x00) i zwrócone dane.</span><span class="sxs-lookup"><span data-stu-id="d8319-1639">**NX_SUCCESS** (0x00) Specified extension OID found and data returned.</span></span>
- <span data-ttu-id="d8319-1640">Napotkano **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0X181) ASN. 1 tag wielobajtowy (nieobsługiwany certyfikat).</span><span class="sxs-lookup"><span data-stu-id="d8319-1640">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="d8319-1641">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) niedozwolone pole ASN. 1 (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="d8319-1641">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="d8319-1642">**NX_SECURE_X509_INVALID_TAG_CLASS** (0X190) Nieprawidłowa Klasa tagu ASN. 1 (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="d8319-1642">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="d8319-1643">Napotkano nieprawidłowe rozszerzenie **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192)</span><span class="sxs-lookup"><span data-stu-id="d8319-1643">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered</span></span>
- <span data-ttu-id="d8319-1644">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) nie znaleziono podanego identyfikatora OID rozszerzenia w podanym certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="d8319-1644">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) The given extension OID was not found in the provided certificate.</span></span>
- <span data-ttu-id="d8319-1645">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik certyfikatu lub rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d8319-1645">**NX_PTR_ERROR** (0x07) Invalid certificate or extension pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1646">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1646">Allowed From</span></span>

<span data-ttu-id="d8319-1647">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1647">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1648">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1648">Example</span></span>

```C
/* Function to parse a Basic Constraints X.509 extension. */
UINT _basic_constraints_extension_parse(NX_SECURE_X509_CERT *certificate)
{
const UCHAR             *current_buffer;
ULONG                    length;
UINT                     status;
NX_SECURE_X509_EXTENSION extension_data;

    /* Find the Basic Constraints extension in the certificate. */
    status = _nx_secure_x509_extension_find(certificate, &extension_data,
                              NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS);

    /* See if extension present - it might be OK if not present! */
    if (status != NX_SUCCESS)
    {
        return(status);
    }

    /* The extension_data structure now points to the raw extension ASN.1
      (DER-encoded). */
    current_buffer = extension_data.nx_secure_x509_extension_data;
    length = extension_data.nx_secure_x509_extension_data_length;

   /* Extension ASN.1 parsing… */

   return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="d8319-1649">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1649">See Also</span></span>

- <span data-ttu-id="d8319-1650">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1650">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="d8319-1651">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="d8319-1651">nx_secure_x509_key_usage_extension_parse</span></span>
- <span data-ttu-id="d8319-1652">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="d8319-1652">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="d8319-1653">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="d8319-1653">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="d8319-1654">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="d8319-1654">nx_secure_x509_extended_key_usage_extension_parse</span></span>

## <a name="nx_secure_x509_key_usage_extension_parse"></a><span data-ttu-id="d8319-1655">nx_secure_x509_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="d8319-1655">nx_secure_x509_key_usage_extension_parse</span></span>

<span data-ttu-id="d8319-1656">Znajdź i Przeanalizuj rozszerzenie użycie klucza X. 509 w certyfikacie X. 509</span><span class="sxs-lookup"><span data-stu-id="d8319-1656">Find and parse an X.509 Key Usage extension in an X.509 certificate</span></span>

### <a name="prototype"></a><span data-ttu-id="d8319-1657">Prototype</span><span class="sxs-lookup"><span data-stu-id="d8319-1657">Prototype</span></span>

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a><span data-ttu-id="d8319-1658">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1658">Description</span></span>

<span data-ttu-id="d8319-1659">Ta usługa jest przeznaczona do wywoływania z poziomu wywołania zwrotnego weryfikacji certyfikatu (zobacz *nx_secure_tls_session_certificate_callback_set)*.</span><span class="sxs-lookup"><span data-stu-id="d8319-1659">This service is intended to be called from within a certificate verification callback (see *nx_secure_tls_session_certificate_callback_set)*.</span></span> <span data-ttu-id="d8319-1660">Wyszuka rozszerzenie użycie klucza i jeśli zostanie znalezione, zwróci pole bitowe użycie klucza w parametrze "pole bitowe".</span><span class="sxs-lookup"><span data-stu-id="d8319-1660">It will search for the Key Usage extension and if found, will return the Key Usage bitfield in the "bitfield" parameter.</span></span>

<span data-ttu-id="d8319-1661">Bity, zgodnie z definicją w specyfikacji X. 509 (RFC 5280), podano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d8319-1661">The bits, as defined by the X.509 specification (RFC 5280) are given in the table below.</span></span> <span data-ttu-id="d8319-1662">Bitowe i z odpowiednią maską bitową (i sprawdzanie dla wartości innej niż zero) będą mieć wartość każdego bitu.</span><span class="sxs-lookup"><span data-stu-id="d8319-1662">A bitwise AND with the appropriate bitmask (and checking for non-zero) will give the value of each bit.</span></span>

<span data-ttu-id="d8319-1663">Należy zauważyć, że kodowanie DER pole bitowe eliminuje dodatkowe zera, więc rzeczywista pozycja bitów w danych pierwotnego certyfikatu będzie prawdopodobnie różna od ich pozycji w zdekodowanym pole bitowe.</span><span class="sxs-lookup"><span data-stu-id="d8319-1663">Note that the DER-encoding of the bitfield eliminates extra zeroes so the actual position of the bits in the raw certificate data will likely be different from their positions in the decoded bitfield.</span></span> <span data-ttu-id="d8319-1664">Podane masek bitowych mają być używane tylko w zdekodowanym pole bitowe zwróconym przez *nx_secure_x509_key_usage_extension_parse* , a nie z danymi certyfikatu z SZYFROWANYm algorytmem DER.</span><span class="sxs-lookup"><span data-stu-id="d8319-1664">The supplied bitmasks are only intended to be used on the decoded bitfield returned by *nx_secure_x509_key_usage_extension_parse* and not with the raw DER-encoded certificate data.</span></span>

<span data-ttu-id="d8319-1665">W wywołaniu zwrotnym weryfikacji certyfikatu Kod powrotu błędu NX_SECURE_X509_KEY_USAGE_ERROR jest zarezerwowany do użytku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8319-1665">In the certificate verification callback, the error return code NX_SECURE_X509_KEY_USAGE_ERROR is reserved for application use.</span></span> <span data-ttu-id="d8319-1666">Jeśli wystąpi błąd podczas sprawdzania użycia klucza, ta wartość może zostać zwrócona z wywołania zwrotnego, aby wskazać przyczynę niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="d8319-1666">If there is an error in checking key usage, this value may be returned from the callback to indicate the reason for failure.</span></span>

| <span data-ttu-id="d8319-1667">Bezpieczny identyfikator NetX</span><span class="sxs-lookup"><span data-stu-id="d8319-1667">NetX Secure Identifier</span></span>                            | <span data-ttu-id="d8319-1668">Pozycja bitowa</span><span class="sxs-lookup"><span data-stu-id="d8319-1668">Bit position</span></span> | <span data-ttu-id="d8319-1669">Opis</span><span class="sxs-lookup"><span data-stu-id="d8319-1669">Description</span></span>                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="d8319-1670">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span><span class="sxs-lookup"><span data-stu-id="d8319-1670">NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE</span></span>  | <span data-ttu-id="d8319-1671">0</span><span class="sxs-lookup"><span data-stu-id="d8319-1671">0</span></span>            | <span data-ttu-id="d8319-1672">Certyfikatu można używać na potrzeby podpisów cyfrowych</span><span class="sxs-lookup"><span data-stu-id="d8319-1672">Certificate can be used for digital signatures</span></span>                                                                                                               |
| <span data-ttu-id="d8319-1673">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span><span class="sxs-lookup"><span data-stu-id="d8319-1673">NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION</span></span>    | <span data-ttu-id="d8319-1674">1</span><span class="sxs-lookup"><span data-stu-id="d8319-1674">1</span></span>            | <span data-ttu-id="d8319-1675">Certyfikat może służyć do weryfikowania podpisów cyfrowych innych niż te dla certyfikatów i list CRL</span><span class="sxs-lookup"><span data-stu-id="d8319-1675">Certificate can be used to verify digital signatures other than those for certificates and CRLs</span></span>                                                              |
| <span data-ttu-id="d8319-1676">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="d8319-1676">NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT</span></span>   | <span data-ttu-id="d8319-1677">2</span><span class="sxs-lookup"><span data-stu-id="d8319-1677">2</span></span>            | <span data-ttu-id="d8319-1678">Certyfikatu można użyć do szyfrowania kluczy symetrycznych (transport kluczy)</span><span class="sxs-lookup"><span data-stu-id="d8319-1678">Certificate can be used to encrypt symmetric keys (key transport)</span></span>                                                                                            |
| <span data-ttu-id="d8319-1679">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span><span class="sxs-lookup"><span data-stu-id="d8319-1679">NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT</span></span>  | <span data-ttu-id="d8319-1680">3</span><span class="sxs-lookup"><span data-stu-id="d8319-1680">3</span></span>            | <span data-ttu-id="d8319-1681">Certyfikatu można użyć do bezpośredniego szyfrowania nieprzetworzonych danych użytkownika (nietypowego)</span><span class="sxs-lookup"><span data-stu-id="d8319-1681">Certificate can be used to directly encrypt raw user data (uncommon)</span></span>                                                                                         |
| <span data-ttu-id="d8319-1682">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span><span class="sxs-lookup"><span data-stu-id="d8319-1682">NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT</span></span>      | <span data-ttu-id="d8319-1683">4</span><span class="sxs-lookup"><span data-stu-id="d8319-1683">4</span></span>            | <span data-ttu-id="d8319-1684">Certyfikat może służyć do uzgadniania kluczy (podobnie jak w przypadku Diffie-Hellmana)</span><span class="sxs-lookup"><span data-stu-id="d8319-1684">Certificate can be used for key agreement (as with Diffie-Hellman)</span></span>                                                                                           |
| <span data-ttu-id="d8319-1685">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span><span class="sxs-lookup"><span data-stu-id="d8319-1685">NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN</span></span>     | <span data-ttu-id="d8319-1686">5</span><span class="sxs-lookup"><span data-stu-id="d8319-1686">5</span></span>            | <span data-ttu-id="d8319-1687">Za pomocą certyfikatu można podpisać i weryfikować inne certyfikaty (certyfikat jest urzędem certyfikacji lub certyfikatem ICA).</span><span class="sxs-lookup"><span data-stu-id="d8319-1687">Certificate can be used to sign and verify other certificates (the certificate is a CA or ICA certificate).</span></span>                                                  |
| <span data-ttu-id="d8319-1688">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span><span class="sxs-lookup"><span data-stu-id="d8319-1688">NX_SECURE_X509_KEY_USAGE_CRL_SIGN</span></span>           | <span data-ttu-id="d8319-1689">6</span><span class="sxs-lookup"><span data-stu-id="d8319-1689">6</span></span>            | <span data-ttu-id="d8319-1690">Klucz publiczny certyfikatu służy do weryfikowania podpisów na listach CRL</span><span class="sxs-lookup"><span data-stu-id="d8319-1690">Certificate public key is used to verify signatures on CRLs</span></span>                                                                                                  |
| <span data-ttu-id="d8319-1691">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="d8319-1691">NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY</span></span>      | <span data-ttu-id="d8319-1692">7</span><span class="sxs-lookup"><span data-stu-id="d8319-1692">7</span></span>            | <span data-ttu-id="d8319-1693">Używany z bitem umów Key (bit 4) — w przypadku ustawienia klucza certyfikatu można używać tylko do szyfrowania podczas uzgadniania klucza.</span><span class="sxs-lookup"><span data-stu-id="d8319-1693">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to encrypt during key agreement.</span></span> <span data-ttu-id="d8319-1694">Niezdefiniowane, jeśli bit umowy klucza nie jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="d8319-1694">Undefined if Key Agreement bit is not set.</span></span> |
| <span data-ttu-id="d8319-1695">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span><span class="sxs-lookup"><span data-stu-id="d8319-1695">NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY</span></span>      | <span data-ttu-id="d8319-1696">8</span><span class="sxs-lookup"><span data-stu-id="d8319-1696">8</span></span>            | <span data-ttu-id="d8319-1697">Używany z bitowym kluczem umowy (bit 4) — w przypadku ustawienia klucza certyfikatu można użyć tylko do odszyfrowania w trakcie uzgadniania klucza.</span><span class="sxs-lookup"><span data-stu-id="d8319-1697">Used with Key Agreement bit (bit 4) – when set, certificate key can only be used to decrypt during key agreement.</span></span> <span data-ttu-id="d8319-1698">Niezdefiniowane, jeśli bit umowy klucza nie jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="d8319-1698">Undefined if Key Agreement bit is not set.</span></span> |

<span data-ttu-id="d8319-1699">Masek bitowych i wartości dla rozszerzenia użycie klucza X. 509</span><span class="sxs-lookup"><span data-stu-id="d8319-1699">Bitmasks and values for X.509 Key Usage Extension</span></span>

### <a name="parameters"></a><span data-ttu-id="d8319-1700">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8319-1700">Parameters</span></span>

- <span data-ttu-id="d8319-1701">**certyfikat** Wskaźnik do zweryfikowanego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d8319-1701">**certificate** Pointer to certificate being verified.</span></span>
- <span data-ttu-id="d8319-1702">**pole bitowe** Zwróć cały pole bitowe z rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d8319-1702">**bitfield** Return the entire bitfield from the extension.</span></span>

### <a name="return-values"></a><span data-ttu-id="d8319-1703">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="d8319-1703">Return Values</span></span>

- <span data-ttu-id="d8319-1704">Znaleziono rozszerzenie użycie klucza **NX_SUCCESS** (0x00) i pole bitowe zwrócone.</span><span class="sxs-lookup"><span data-stu-id="d8319-1704">**NX_SUCCESS** (0x00) Key usage extension found and bitfield returned.</span></span>
- <span data-ttu-id="d8319-1705">Napotkano **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0X181) ASN. 1 tag wielobajtowy (nieobsługiwany certyfikat).</span><span class="sxs-lookup"><span data-stu-id="d8319-1705">**NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** (0x181) ASN.1 multi-byte tag encountered (unsupported certificate).</span></span>
- <span data-ttu-id="d8319-1706">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) niedozwolone pole ASN. 1 (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="d8319-1706">**NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** (0x182) Invaild ASN.1 field encountered (invalid certificate).</span></span>
- <span data-ttu-id="d8319-1707">**NX_SECURE_X509_INVALID_TAG_CLASS** (0X190) Nieprawidłowa Klasa tagu ASN. 1 (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="d8319-1707">**NX_SECURE_X509_INVALID_TAG_CLASS** (0x190) Invalid ASN.1 tag class encountered (invalid certificate).</span></span>
- <span data-ttu-id="d8319-1708">Napotkano nieprawidłowe rozszerzenie **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) (nieprawidłowy certyfikat).</span><span class="sxs-lookup"><span data-stu-id="d8319-1708">**NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** (0x192) Invalid extension encountered (invalid certificate).</span></span>
- <span data-ttu-id="d8319-1709">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B) nie znaleziono rozszerzenia użycie klucza w podanym certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="d8319-1709">**NX_SECURE_X509_EXTENSION_NOT_FOUND** (0x19B)The Key Usage extension was not found in the provided certificate.</span></span>
- <span data-ttu-id="d8319-1710">**NX_PTR_ERROR** (0X07) nieprawidłowy certyfikat lub wskaźnik pole bitowe.</span><span class="sxs-lookup"><span data-stu-id="d8319-1710">**NX_PTR_ERROR** (0x07) Invalid certificate or bitfield pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d8319-1711">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="d8319-1711">Allowed From</span></span>

<span data-ttu-id="d8319-1712">Wątki</span><span class="sxs-lookup"><span data-stu-id="d8319-1712">Threads</span></span>

### <a name="example"></a><span data-ttu-id="d8319-1713">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8319-1713">Example</span></span>

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session,
  NX_SECURE_X509_CERT* certificate)
{
UINT status;
USHORT key_usage_bitfield;

    /* Key usage – extract key usage bitfield. */
    status = nx_secure_x509_key_usage_extension_parse(certificate, &key_usage_bitfield);

   /* Check certificate for a few specific key usage bits. */
   if((key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE) == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION)   == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT)  == 0)
    {
        printf("Expected key usage bitfield bits not set!\n");
        return(NX_SECURE_X509_KEY_USAGE_ERROR);
    }

    /* The specified bits were set, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a><span data-ttu-id="d8319-1714">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8319-1714">See Also</span></span>

- <span data-ttu-id="d8319-1715">nx_secure_tls_session_certificate_callback_set</span><span class="sxs-lookup"><span data-stu-id="d8319-1715">nx_secure_tls_session_certificate_callback_set</span></span>
- <span data-ttu-id="d8319-1716">nx_secure_x509_extended_key_usage_extension_parse</span><span class="sxs-lookup"><span data-stu-id="d8319-1716">nx_secure_x509_extended_key_usage_extension_parse</span></span>
- <span data-ttu-id="d8319-1717">nx_secure_x509_crl_revocation_check</span><span class="sxs-lookup"><span data-stu-id="d8319-1717">nx_secure_x509_crl_revocation_check</span></span>
- <span data-ttu-id="d8319-1718">nx_secure_x509_common_name_dns_check</span><span class="sxs-lookup"><span data-stu-id="d8319-1718">nx_secure_x509_common_name_dns_check</span></span>
- <span data-ttu-id="d8319-1719">nx_secure_x509_extension_find</span><span class="sxs-lookup"><span data-stu-id="d8319-1719">nx_secure_x509_extension_find</span></span>
