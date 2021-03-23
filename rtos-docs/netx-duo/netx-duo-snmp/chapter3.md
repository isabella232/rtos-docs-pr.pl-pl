---
title: Rozdział 3 — Opis usług Azure RTO NetX Duo SNMP Agent
description: Ten rozdział zawiera opis wszystkich usług agenta SNMP NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf4c4cb0edb7deb7bd0f257f48949b5c7355426b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821672"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a><span data-ttu-id="aa55c-103">Rozdział 3 — Opis usług Azure RTO NetX Duo SNMP Agent</span><span class="sxs-lookup"><span data-stu-id="aa55c-103">Chapter 3 - Description of Azure RTOS NetX Duo SNMP agent services</span></span>

<span data-ttu-id="aa55c-104">Ten rozdział zawiera opis wszystkich usług agenta SNMP usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="aa55c-104">This chapter contains a description of all Azure RTOS NetX Duo SNMP agent services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="aa55c-105">W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="aa55c-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- [<span data-ttu-id="aa55c-106">nx_snmp_agent_auth_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="aa55c-106">nx_snmp_agent_auth_trap_key_use</span></span>](#nx_snmp_agent_auth_trap_key_use)
   - <span data-ttu-id="aa55c-107">*Określ klucz uwierzytelniania (tylko protokół SNMP v3) dla komunikatów pułapki*</span><span class="sxs-lookup"><span data-stu-id="aa55c-107">*Specify authentication key (SNMP v3 only) for trap messages*</span></span>
- [<span data-ttu-id="aa55c-108">nx_snmp_agent_authenticate_key_use</span><span class="sxs-lookup"><span data-stu-id="aa55c-108">nx_snmp_agent_authenticate_key_use</span></span>](#nx_snmp_agent_authenticate_key_use)
   - <span data-ttu-id="aa55c-109">*Określ klucz uwierzytelniania (tylko protokół SNMP v3) dla komunikatów odpowiedzi*</span><span class="sxs-lookup"><span data-stu-id="aa55c-109">*Specify authentication key (SNMP v3 only) for response messages*</span></span>
- [<span data-ttu-id="aa55c-110">nx_snmp_agent_community_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-110">nx_snmp_agent_community_get</span></span>](#nx_snmp_agent_community_get)
   - <span data-ttu-id="aa55c-111">*Pobierz nazwę społeczności*</span><span class="sxs-lookup"><span data-stu-id="aa55c-111">*Retrieve community name*</span></span>
- [<span data-ttu-id="aa55c-112">nx_snmp_agent_context_engine_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-112">nx_snmp_agent_context_engine_set</span></span>](#nx_snmp_agent_context_engine_set)
   - <span data-ttu-id="aa55c-113">*Ustaw aparat kontekstu (tylko protokół SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-113">*Set context engine (SNMP v3 only)*</span></span>
- [<span data-ttu-id="aa55c-114">nx_snmp_agent_context_name_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-114">nx_snmp_agent_context_name_set</span></span>](#nx_snmp_agent_context_name_set)
   - <span data-ttu-id="aa55c-115">*Ustaw nazwę kontekstu (tylko protokół SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-115">*Set context name (SNMP v3 only)*</span></span>
- [<span data-ttu-id="aa55c-116">nx_snmp_agent_create</span><span class="sxs-lookup"><span data-stu-id="aa55c-116">nx_snmp_agent_create</span></span>](#nx_snmp_agent_create)
   - <span data-ttu-id="aa55c-117">*Utwórz agenta SNMP*</span><span class="sxs-lookup"><span data-stu-id="aa55c-117">*Create SNMP agent*</span></span>
- [<span data-ttu-id="aa55c-118">nx_snmp_agent_current_version_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-118">nx_snmp_agent_current_version_get</span></span>](#nx_snmp_agent_current_version_get)
   - <span data-ttu-id="aa55c-119">*Pobierz wersję protokołu SNMP odebranego pakietu*</span><span class="sxs-lookup"><span data-stu-id="aa55c-119">*Get the SNMP version of received packet*</span></span>
- [<span data-ttu-id="aa55c-120">nx_snmp_agent_request_get_type_test</span><span class="sxs-lookup"><span data-stu-id="aa55c-120">nx_snmp_agent_request_get_type_test</span></span>](#nx_snmp_agent_request_get_type_test)
   - <span data-ttu-id="aa55c-121">*Wskaż, czy ostatnie żądanie SNMP ma typ GET lub SET*</span><span class="sxs-lookup"><span data-stu-id="aa55c-121">*Indicate if last SNMP request is GET or SET type*</span></span>
- [<span data-ttu-id="aa55c-122">nx_snmp_agent_private_string_test</span><span class="sxs-lookup"><span data-stu-id="aa55c-122">nx_snmp_agent_private_string_test</span></span>](#nx_snmp_agent_private_string_test)
   - <span data-ttu-id="aa55c-123">*Określ, czy ciąg jest zgodny z prywatnym ciągiem agenta*</span><span class="sxs-lookup"><span data-stu-id="aa55c-123">*Determine if string matches agent private string*</span></span>
- [<span data-ttu-id="aa55c-124">nx_snmp_agent_public_string_test</span><span class="sxs-lookup"><span data-stu-id="aa55c-124">nx_snmp_agent_public_string_test</span></span>](#nx_snmp_agent_public_string_test)
   - <span data-ttu-id="aa55c-125">*Określ, czy ciąg jest zgodny z publicznym ciągiem agenta*</span><span class="sxs-lookup"><span data-stu-id="aa55c-125">*Determine if string matches agent public string*</span></span>
- [<span data-ttu-id="aa55c-126">nx_snmp_agent_set_interface</span><span class="sxs-lookup"><span data-stu-id="aa55c-126">nx_snmp_agent_set_interface</span></span>](#nx_snmp_agent_set_interface)
   - <span data-ttu-id="aa55c-127">*Ustawianie interfejsu sieciowego dla obsługi komunikatów SNMP*</span><span class="sxs-lookup"><span data-stu-id="aa55c-127">*Set network interface for SNMP messaging*</span></span>
- [<span data-ttu-id="aa55c-128">nx_snmp_agent_private_string_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-128">nx_snmp_agent_private_string_set</span></span>](#nx_snmp_agent_private_string_set)
   - <span data-ttu-id="aa55c-129">*Ustaw ciąg społeczności prywatnej agenta SNMP*</span><span class="sxs-lookup"><span data-stu-id="aa55c-129">*Set the SNMP agent private community string*</span></span>
- [<span data-ttu-id="aa55c-130">nx_snmp_agent_public_string_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-130">nx_snmp_agent_public_string_set</span></span>](#nx_snmp_agent_public_string_set)
   - <span data-ttu-id="aa55c-131">*Ustaw publiczny ciąg społeczności agenta SNMP*</span><span class="sxs-lookup"><span data-stu-id="aa55c-131">*Set the SNMP agent public community string*</span></span>
- [<span data-ttu-id="aa55c-132">nx_snmp_agent_version_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-132">nx_snmp_agent_version_set</span></span>](#nx_snmp_agent_version_set)
   - <span data-ttu-id="aa55c-133">*Ustaw stan agenta SNMP dla wszystkich wersji SNMP*</span><span class="sxs-lookup"><span data-stu-id="aa55c-133">*Set the SNMP agent status for all SNMP versions*</span></span>
- [<span data-ttu-id="aa55c-134">nx_snmp_agent_delete</span><span class="sxs-lookup"><span data-stu-id="aa55c-134">nx_snmp_agent_delete</span></span>](#nx_snmp_agent_delete)
   - <span data-ttu-id="aa55c-135">*Usuń agenta SNMP*</span><span class="sxs-lookup"><span data-stu-id="aa55c-135">*Delete SNMP agent*</span></span>
- [<span data-ttu-id="aa55c-136">nx_snmp_agent_md5_key_create</span><span class="sxs-lookup"><span data-stu-id="aa55c-136">nx_snmp_agent_md5_key_create</span></span>](#nx_snmp_agent_md5_key_create)
   - <span data-ttu-id="aa55c-137">*Utwórz klucz MD5 (tylko protokół SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-137">*Create md5 key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="aa55c-138">nx_snmp_agent_md5_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="aa55c-138">nx_snmp_agent_md5_key_create_extended</span></span>](#nx_snmp_agent_md5_key_create_extended)
   - <span data-ttu-id="aa55c-139">*Utwórz klucz MD5 (tylko protokół SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-139">*Create md5 key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="aa55c-140">nx_snmp_agent_priv_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="aa55c-140">nx_snmp_agent_priv_trap_key_use</span></span>](#nx_snmp_agent_priv_trap_key_use)
   - <span data-ttu-id="aa55c-141">*Określ klucz szyfrowania (tylko protokół SNMP v3) dla komunikatów pułapki*</span><span class="sxs-lookup"><span data-stu-id="aa55c-141">*Specify encryption key (SNMP v3 only) for trap messages*</span></span>
- [<span data-ttu-id="aa55c-142">nx_snmp_agent_privacy_key_use</span><span class="sxs-lookup"><span data-stu-id="aa55c-142">nx_snmp_agent_privacy_key_use</span></span>](#nx_snmp_agent_privacy_key_use)
   - <span data-ttu-id="aa55c-143">*Określ klucz szyfrowania (tylko protokół SNMP v3) dla komunikatów odpowiedzi*</span><span class="sxs-lookup"><span data-stu-id="aa55c-143">*Specify encryption key (SNMP v3 only) for response messages*</span></span>
- [<span data-ttu-id="aa55c-144">nx_snmp_agent_sha_key_create</span><span class="sxs-lookup"><span data-stu-id="aa55c-144">nx_snmp_agent_sha_key_create</span></span>](#nx_snmp_agent_sha_key_create)
   - <span data-ttu-id="aa55c-145">*Utwórz klucz SHA (tylko protokół SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-145">*Create sha key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="aa55c-146">nx_snmp_agent_sha_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="aa55c-146">nx_snmp_agent_sha_key_create_extended</span></span>](#nx_snmp_agent_sha_key_create_extended)
   - <span data-ttu-id="aa55c-147">*Utwórz klucz SHA (tylko protokół SNMP v3)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-147">*Create sha key (SNMP v3 only)*</span></span>
- [<span data-ttu-id="aa55c-148">nx_snmp_agent_start</span><span class="sxs-lookup"><span data-stu-id="aa55c-148">nx_snmp_agent_start</span></span>](#nx_snmp_agent_start)
   - <span data-ttu-id="aa55c-149">*Uruchom agenta SNMP*</span><span class="sxs-lookup"><span data-stu-id="aa55c-149">*Start SNMP agent*</span></span>
- [<span data-ttu-id="aa55c-150">nx_snmp_agent_stop</span><span class="sxs-lookup"><span data-stu-id="aa55c-150">nx_snmp_agent_stop</span></span>](#nx_snmp_agent_stop)
   - <span data-ttu-id="aa55c-151">*Zatrzymaj agenta SNMP*</span><span class="sxs-lookup"><span data-stu-id="aa55c-151">*Stop SNMP agent*</span></span>
- [<span data-ttu-id="aa55c-152">nx_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-152">nx_snmp_agent_trap_send</span></span>](#nx_snmp_agent_trap_send)
   - <span data-ttu-id="aa55c-153">*Wyślij pułapkę SNMP v1 (tylko IPv4)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-153">*Send SNMP v1 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="aa55c-154">nx_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-154">nx_snmp_agent_trapv2_send</span></span>](#nx_snmp_agent_trapv2_send)
   - <span data-ttu-id="aa55c-155">*Wyślij pułapkę SNMP v2 (tylko IPv4)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-155">*Send SNMP v2 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="aa55c-156">nx_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-156">nx_snmp_agent_trapv2_oid_send</span></span>](#nx_snmp_agent_trapv2_oid_send)
   - <span data-ttu-id="aa55c-157">*Wyślij pułapkę SNMP v2 (tylko IPv4) określającą identyfikator OID*</span><span class="sxs-lookup"><span data-stu-id="aa55c-157">*Send SNMP v2 trap (IPv4 only) specifying the OID*</span></span>
- [<span data-ttu-id="aa55c-158">nx_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-158">nx_snmp_agent_trapv3_send</span></span>](#nx_snmp_agent_trapv3_send)
   - <span data-ttu-id="aa55c-159">*Wyślij pułapkę SNMP v3 (tylko IPv4)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-159">*Send SNMP v3 trap (IPv4 only)*</span></span>
- [<span data-ttu-id="aa55c-160">nx_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-160">nx_snmp_agent_trapv3_oid_send</span></span>](#nx_snmp_agent_trapv3_oid_send)
   - <span data-ttu-id="aa55c-161">*Wyślij pułapkę SNMP v2 (tylko IPv4) określającą identyfikator OID*</span><span class="sxs-lookup"><span data-stu-id="aa55c-161">*Send SNMP v2 trap (IPv4 only) specifying the OID*</span></span>
- [<span data-ttu-id="aa55c-162">nxd_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-162">nxd_snmp_agent_trap_send</span></span>](#nxd_snmp_agent_trap_send)
   - <span data-ttu-id="aa55c-163">*Wyślij pułapkę SNMP v1 (IPv4 i IPv6)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-163">*Send SNMP v1 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="aa55c-164">nxd_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-164">nxd_snmp_agent_trapv2_send</span></span>](#nxd_snmp_agent_trapv2_send)
   - <span data-ttu-id="aa55c-165">*Wyślij pułapkę SNMP v2 (IPv4 i IPv6)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-165">*Send SNMP v2 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="aa55c-166">nxd_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-166">nxd_snmp_agent_trapv2_oid_send</span></span>](#nxd_snmp_agent_trapv2_oid_send)
   - <span data-ttu-id="aa55c-167">*Wyślij pułapkę SNMP v2 (IPv4/IPv6) określającą identyfikator OID*</span><span class="sxs-lookup"><span data-stu-id="aa55c-167">*Send SNMP v2 trap (IPv4/IPv6) specifying the OID*</span></span>
- [<span data-ttu-id="aa55c-168">nxd_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-168">nxd_snmp_agent_trapv3_send</span></span>](#nxd_snmp_agent_trapv3_send)
   - <span data-ttu-id="aa55c-169">*Wyślij pułapkę SNMP v3 (IPv4 i IPv6)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-169">*Send SNMP v3 trap (IPv4 and IPv6)*</span></span>
- [<span data-ttu-id="aa55c-170">nxd_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-170">nxd_snmp_agent_trapv3_oid_send</span></span>](#nxd_snmp_agent_trapv3_oid_send)
   - <span data-ttu-id="aa55c-171">*Wyślij pułapkę SNMP v2 (IPv4/IPv6) określającą identyfikator OID*</span><span class="sxs-lookup"><span data-stu-id="aa55c-171">*Send SNMP v2 trap (IPv4/IPv6) specifying the OID*</span></span>
- [<span data-ttu-id="aa55c-172">nx_snmp_agent_v3_context_boots_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-172">nx_snmp_agent_v3_context_boots_set</span></span>](#nx_snmp_agent_v3_context_boots_set)
   - <span data-ttu-id="aa55c-173">*Ustaw liczbę ponownych uruchomień*</span><span class="sxs-lookup"><span data-stu-id="aa55c-173">*Set the number of reboots*</span></span>
- [<span data-ttu-id="aa55c-174">nx_snmp_object_compare</span><span class="sxs-lookup"><span data-stu-id="aa55c-174">nx_snmp_object_compare</span></span>](#nx_snmp_object_compare)
   - <span data-ttu-id="aa55c-175">*Porównaj dwa obiekty*</span><span class="sxs-lookup"><span data-stu-id="aa55c-175">*Compare two objects*</span></span>
- [<span data-ttu-id="aa55c-176">nx_snmp_object_compare_extended</span><span class="sxs-lookup"><span data-stu-id="aa55c-176">nx_snmp_object_compare_extended</span></span>](#nx_snmp_object_compare_extended)
   - <span data-ttu-id="aa55c-177">*Porównaj dwa obiekty*</span><span class="sxs-lookup"><span data-stu-id="aa55c-177">*Compare two objects*</span></span>
- [<span data-ttu-id="aa55c-178">nx_snmp_object_copy</span><span class="sxs-lookup"><span data-stu-id="aa55c-178">nx_snmp_object_copy</span></span>](#nx_snmp_object_copy)
   - <span data-ttu-id="aa55c-179">*Kopiowanie obiektu*</span><span class="sxs-lookup"><span data-stu-id="aa55c-179">*Copy an object*</span></span>
- [<span data-ttu-id="aa55c-180">nx_snmp_object_copy_extended</span><span class="sxs-lookup"><span data-stu-id="aa55c-180">nx_snmp_object_copy_extended</span></span>](#nx_snmp_object_copy_extended)
   - <span data-ttu-id="aa55c-181">*Kopiowanie obiektu*</span><span class="sxs-lookup"><span data-stu-id="aa55c-181">*Copy an object*</span></span>
- [<span data-ttu-id="aa55c-182">nx_snmp_object_counter_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-182">nx_snmp_object_counter_get</span></span>](#nx_snmp_object_counter_get)
   - <span data-ttu-id="aa55c-183">*Pobierz obiekt licznika*</span><span class="sxs-lookup"><span data-stu-id="aa55c-183">*Get counter object*</span></span>
- [<span data-ttu-id="aa55c-184">nx_snmp_object_counter_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-184">nx_snmp_object_counter_set</span></span>](#nx_snmp_object_counter_set)
   - <span data-ttu-id="aa55c-185">*Ustaw obiekt licznika*</span><span class="sxs-lookup"><span data-stu-id="aa55c-185">*Set counter object*</span></span>
- [<span data-ttu-id="aa55c-186">nx_snmp_object_counter64_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-186">nx_snmp_object_counter64_get</span></span>](#nx_snmp_object_counter64_get)
   - <span data-ttu-id="aa55c-187">*Pobierz 64-bitowy obiekt licznika*</span><span class="sxs-lookup"><span data-stu-id="aa55c-187">*Get 64-bit counter object*</span></span>
- [<span data-ttu-id="aa55c-188">nx_snmp_object_counter64_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-188">nx_snmp_object_counter64_set</span></span>](#nx_snmp_object_counter64_set)
   - <span data-ttu-id="aa55c-189">*Ustaw 64-bitowy obiekt licznika*</span><span class="sxs-lookup"><span data-stu-id="aa55c-189">*Set 64-bit counter object*</span></span>
- [<span data-ttu-id="aa55c-190">nx_snmp_object_end_of_mib</span><span class="sxs-lookup"><span data-stu-id="aa55c-190">nx_snmp_object_end_of_mib</span></span>](#nx_snmp_object_end_of_mib)
   - <span data-ttu-id="aa55c-191">*Ustaw wartość końca MIB*</span><span class="sxs-lookup"><span data-stu-id="aa55c-191">*Set end-of-mib value*</span></span>
- [<span data-ttu-id="aa55c-192">nx_snmp_object_gauge_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-192">nx_snmp_object_gauge_get</span></span>](#nx_snmp_object_gauge_get)
   - <span data-ttu-id="aa55c-193">*Pobierz obiekt miernika*</span><span class="sxs-lookup"><span data-stu-id="aa55c-193">*Get gauge object*</span></span>
- [<span data-ttu-id="aa55c-194">nx_snmp_object_gauge_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-194">nx_snmp_object_gauge_set</span></span>](#nx_snmp_object_gauge_set)
   - <span data-ttu-id="aa55c-195">*Ustaw obiekt miernika*</span><span class="sxs-lookup"><span data-stu-id="aa55c-195">*Set gauge object*</span></span>
- [<span data-ttu-id="aa55c-196">nx_snmp_object_id_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-196">nx_snmp_object_id_get</span></span>](#nx_snmp_object_id_get)
   - <span data-ttu-id="aa55c-197">*Pobierz identyfikator obiektu*</span><span class="sxs-lookup"><span data-stu-id="aa55c-197">*Get object id*</span></span>
- [<span data-ttu-id="aa55c-198">nx_snmp_object_id_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-198">nx_snmp_object_id_set</span></span>](#nx_snmp_object_id_set)
   - <span data-ttu-id="aa55c-199">*Ustaw identyfikator obiektu*</span><span class="sxs-lookup"><span data-stu-id="aa55c-199">*Set object id*</span></span>
- [<span data-ttu-id="aa55c-200">nx_snmp_object_integer_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-200">nx_snmp_object_integer_get</span></span>](#nx_snmp_object_integer_get)
   - <span data-ttu-id="aa55c-201">*Pobierz obiekt typu Integer*</span><span class="sxs-lookup"><span data-stu-id="aa55c-201">*Get integer object*</span></span>
- [<span data-ttu-id="aa55c-202">nx_snmp_object_integer_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-202">nx_snmp_object_integer_set</span></span>](#nx_snmp_object_integer_set)
   - <span data-ttu-id="aa55c-203">*Ustaw obiekt liczb całkowitych*</span><span class="sxs-lookup"><span data-stu-id="aa55c-203">*Set integer object*</span></span>
- [<span data-ttu-id="aa55c-204">nx_snmp_object_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-204">nx_snmp_object_ip_address_get</span></span>](#nx_snmp_object_ip_address_get)
   - <span data-ttu-id="aa55c-205">*Pobierz obiekt adresu IP (tylko IPv4)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-205">*Get IP address object (IPv4 only)*</span></span>
- [<span data-ttu-id="aa55c-206">nx_snmp_object_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-206">nx_snmp_object_ip_address_set</span></span>](#nx_snmp_object_ip_address_set)
   - <span data-ttu-id="aa55c-207">*Ustawianie obiektu adresu IP (tylko IPv4)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-207">*Set IP address object (IPv4 only)*</span></span>
- [<span data-ttu-id="aa55c-208">nx_snmp_object_ipv6_address_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-208">nx_snmp_object_ipv6_address_get</span></span>](#nx_snmp_object_ipv6_address_get)
   - <span data-ttu-id="aa55c-209">*Pobieranie obiektu adresu IP (tylko protokół IPv6)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-209">*Get IP address object (IPv6 only)*</span></span>
- [<span data-ttu-id="aa55c-210">nx_snmp_object_ipv6_address_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-210">nx_snmp_object_ipv6_address_set</span></span>](#nx_snmp_object_ipv6_address_set)
   - <span data-ttu-id="aa55c-211">*Ustawianie obiektu adresu IP (tylko protokół IPv6)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-211">*Set IP address object (IPv6 only)*</span></span>
- [<span data-ttu-id="aa55c-212">nx_snmp_object_no_instance</span><span class="sxs-lookup"><span data-stu-id="aa55c-212">nx_snmp_object_no_instance</span></span>](#nx_snmp_object_no_instance)
   - <span data-ttu-id="aa55c-213">*Ustaw wartość bez wystąpienia*</span><span class="sxs-lookup"><span data-stu-id="aa55c-213">*Set no-instance value*</span></span>
- [<span data-ttu-id="aa55c-214">nx_snmp_object_not_found</span><span class="sxs-lookup"><span data-stu-id="aa55c-214">nx_snmp_object_not_found</span></span>](#nx_snmp_object_not_found)
   - <span data-ttu-id="aa55c-215">*Ustaw wartość nie znaleziono*</span><span class="sxs-lookup"><span data-stu-id="aa55c-215">*Set not-found value*</span></span>
- [<span data-ttu-id="aa55c-216">nx_snmp_object_octet_string_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-216">nx_snmp_object_octet_string_get</span></span>](#nx_snmp_object_octet_string_get)
   - <span data-ttu-id="aa55c-217">*Pobieranie obiektu ciągu oktetowego*</span><span class="sxs-lookup"><span data-stu-id="aa55c-217">*Get octet string object*</span></span>
- [<span data-ttu-id="aa55c-218">nx_snmp_object_octet_string_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-218">nx_snmp_object_octet_string_set</span></span>](#nx_snmp_object_octet_string_set)
   - <span data-ttu-id="aa55c-219">*Ustawianie obiektu ciągu oktetowego*</span><span class="sxs-lookup"><span data-stu-id="aa55c-219">*Set octet string object*</span></span>
- [<span data-ttu-id="aa55c-220">nx_snmp_object_string_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-220">nx_snmp_object_string_get</span></span>](#nx_snmp_object_string_get)
   - <span data-ttu-id="aa55c-221">*Pobierz obiekt ciągu ASCII*</span><span class="sxs-lookup"><span data-stu-id="aa55c-221">*Get ASCII string object*</span></span>
- [<span data-ttu-id="aa55c-222">nx_snmp_object_string_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-222">nx_snmp_object_string_set</span></span>](#nx_snmp_object_string_set)
   - <span data-ttu-id="aa55c-223">*Ustaw obiekt ciągu ASCII*</span><span class="sxs-lookup"><span data-stu-id="aa55c-223">*Set ASCII string object*</span></span>
- [<span data-ttu-id="aa55c-224">nx_snmp_object_timetics_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-224">nx_snmp_object_timetics_get</span></span>](#nx_snmp_object_timetics_get)
   - <span data-ttu-id="aa55c-225">*Pobierz obiekt timetics*</span><span class="sxs-lookup"><span data-stu-id="aa55c-225">*Get timetics object*</span></span>
- [<span data-ttu-id="aa55c-226">nx_snmp_object_timetics_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-226">nx_snmp_object_timetics_set</span></span>](#nx_snmp_object_timetics_set)
   - <span data-ttu-id="aa55c-227">*Ustaw obiekt timetics*</span><span class="sxs-lookup"><span data-stu-id="aa55c-227">*Set timetics object*</span></span>

## <a name="nx_snmp_agent_auth_trap_key_use"></a><span data-ttu-id="aa55c-228">nx_snmp_agent_auth_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="aa55c-228">nx_snmp_agent_auth_trap_key_use</span></span>
<span data-ttu-id="aa55c-229">Określ klucz uwierzytelniania dla komunikatów pułapki</span><span class="sxs-lookup"><span data-stu-id="aa55c-229">Specify authentication key for trap messages</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-230">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-230">Prototype</span></span>

```c
UINT nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="aa55c-231">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-231">Description</span></span>

<span data-ttu-id="aa55c-232">Ta usługa określa klucz, który ma być używany do ustawiania parametrów uwierzytelniania w nagłówku zabezpieczeń SNMPv3 w komunikatach pułapki.</span><span class="sxs-lookup"><span data-stu-id="aa55c-232">This service specifies the key to be used for setting authentication parameters in the SNMPv3 security header in trap messages.</span></span> <span data-ttu-id="aa55c-233">Podanie wartości NX_NULL klucza powoduje wyłączenie uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="aa55c-233">Supplying a NX_NULL value for the key disables authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="aa55c-234">Należy wcześniej utworzyć klucz.</span><span class="sxs-lookup"><span data-stu-id="aa55c-234">The key must be previously created.</span></span> <span data-ttu-id="aa55c-235">Zobacz nx_snmp_agent_md5_key_create lub nx_snmp_agent_sha_key_create.</span><span class="sxs-lookup"><span data-stu-id="aa55c-235">See nx_snmp_agent_md5_key_create or nx_snmp_agent_sha_key_create.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-236">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-236">Input Parameters</span></span>

- <span data-ttu-id="aa55c-237">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-237">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-238">**klucz** Wskaźnik do wcześniej utworzonego klucza MD5 lub SHA.</span><span class="sxs-lookup"><span data-stu-id="aa55c-238">**key** Pointer to a previously created MD5 or SHA key.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-239">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-239">Return Values</span></span>

- <span data-ttu-id="aa55c-240">**NX_SUCCESS** (0x00) — pomyślne uwierzytelnianie zestawu kluczy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-240">**NX_SUCCESS** (0x00) Successful authentication key set.</span></span>
- <span data-ttu-id="aa55c-241">**NX_NOT_ENABLED** (0X14) zabezpieczenia protokołu SNMP wyłączone</span><span class="sxs-lookup"><span data-stu-id="aa55c-241">**NX_NOT_ENABLED** (0x14) SNMP Security disabled</span></span> 
- <span data-ttu-id="aa55c-242">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-242">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-243">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-243">Allowed From</span></span>

<span data-ttu-id="aa55c-244">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-244">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-245">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-245">Example</span></span>

```c
/* Use previously created “my_key” for SNMPv3 trap message authentication.  */
status =  nx_snmp_agent_auth_trap_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for authentication parameters in trap messages.  */
```

## <a name="nx_snmp_agent_authenticate_key_use"></a><span data-ttu-id="aa55c-246">nx_snmp_agent_authenticate_key_use</span><span class="sxs-lookup"><span data-stu-id="aa55c-246">nx_snmp_agent_authenticate_key_use</span></span>
<span data-ttu-id="aa55c-247">Określ klucz uwierzytelniania dla komunikatów odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="aa55c-247">Specify authentication key for response messages</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-248">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-248">Prototype</span></span>

```c
UINT nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr, 
                                        NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="aa55c-249">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-249">Description</span></span>

<span data-ttu-id="aa55c-250">Ta usługa określa klucz, który ma być używany dla parametrów uwierzytelniania w parametrze zabezpieczeń SNMPv3 dla wszystkich żądań wykonanych po jej ustawieniu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-250">This service specifies the key to be used for authentication parameters in the SNMPv3 security parameter for all requests made after it is set.</span></span> <span data-ttu-id="aa55c-251">Podanie wartości NX_NULL klucza powoduje wyłączenie uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="aa55c-251">Supplying a NX_NULL value for the key disables authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="aa55c-252">Należy wcześniej utworzyć klucz.</span><span class="sxs-lookup"><span data-stu-id="aa55c-252">The key must be previously created.</span></span> <span data-ttu-id="aa55c-253">Zobacz nx_snmp_agent_md5_key_create lub nx_snmp_agent_sha_key_create.</span><span class="sxs-lookup"><span data-stu-id="aa55c-253">See nx_snmp_agent_md5_key_create or nx_snmp_agent_sha_key_create.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-254">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-254">Input Parameters</span></span>

- <span data-ttu-id="aa55c-255">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-255">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-256">**klucz** Wskaźnik do wcześniej utworzonego klucza MD5 lub SHA.</span><span class="sxs-lookup"><span data-stu-id="aa55c-256">**key** Pointer to a previously created MD5 or SHA key.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-257">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-257">Return Values</span></span>

- <span data-ttu-id="aa55c-258">**NX_SUCCESS** (0X00) pomyślnie ustawiono klucz SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-258">**NX_SUCCESS** (0x00) Successful SNMP key set.</span></span>
- <span data-ttu-id="aa55c-259">**NX_NOT_ENABLED** (0X14) zabezpieczenia protokołu SNMP wyłączone</span><span class="sxs-lookup"><span data-stu-id="aa55c-259">**NX_NOT_ENABLED** (0x14) SNMP Security disabled</span></span>
- <span data-ttu-id="aa55c-260">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-260">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-261">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-261">Allowed From</span></span>

<span data-ttu-id="aa55c-262">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-262">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-263">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-263">Example</span></span>

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a><span data-ttu-id="aa55c-264">nx_snmp_agent_community_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-264">nx_snmp_agent_community_get</span></span>
<span data-ttu-id="aa55c-265">Pobierz nazwę społeczności</span><span class="sxs-lookup"><span data-stu-id="aa55c-265">Retrieve community name</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-266">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-266">Prototype</span></span>

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a><span data-ttu-id="aa55c-267">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-267">Description</span></span>

<span data-ttu-id="aa55c-268">Ta usługa Pobiera nazwę społeczności z najnowszego żądania SNMP otrzymanego przez agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-268">This service retrieves the community name from the most recent SNMP request received by the SNMP Agent.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-269">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-269">Input Parameters</span></span>

- <span data-ttu-id="aa55c-270">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-270">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-271">**community_string_ptr** Wskaźnik na wskaźnik ciągu, aby zwrócić ciąg identyfikacyjny agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-271">**community_string_ptr** Pointer to a string pointer to return the SNMP Agent community string.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-272">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-272">Return Values</span></span>

- <span data-ttu-id="aa55c-273">**NX_SUCCESS** (0X00) pomyślnie pobiera społeczność SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-273">**NX_SUCCESS** (0x00) Successful SNMP community get.</span></span>
- <span data-ttu-id="aa55c-274">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-274">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-275">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-275">Allowed From</span></span>

<span data-ttu-id="aa55c-276">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-276">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-277">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-277">Example</span></span>

```c
UCHAR *string_ptr;

/* Pickup the community string pointer for my_agent.  */
status =  nx_snmp_agent_community_get(&my_agent, &string_ptr);


/* If status is NX_SUCCESS the pointer “string_ptr” points to the
   last community name supplied to the SNMP agent.  */
```

## <a name="nx_snmp_agent_request_get_type_test"></a><span data-ttu-id="aa55c-278">nx_snmp_agent_request_get_type_test</span><span class="sxs-lookup"><span data-stu-id="aa55c-278">nx_snmp_agent_request_get_type_test</span></span>
<span data-ttu-id="aa55c-279">Wskaż, czy ostatnie żądanie SNMP ma typ GET lub SET</span><span class="sxs-lookup"><span data-stu-id="aa55c-279">Indicate if last SNMP request is GET or SET type</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-280">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-280">Prototype</span></span>

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

### <a name="description"></a><span data-ttu-id="aa55c-281">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-281">Description</span></span>

<span data-ttu-id="aa55c-282">Ta usługa wskazuje, czy najnowsze żądanie od menedżera SNMP to GET (GET, GetNext lub GetBulk) lub typu zestawu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-282">This service indicates if the most recent request from the SNMP Manager is a GET (GET, GETNEXT, or GETBULK) or SET type.</span></span> <span data-ttu-id="aa55c-283">Jest ona przeznaczona do użycia z wywołaniem zwrotnym nazwy użytkownika, w którym aplikacja SNMPv1 lub SNMPv2 będzie chcieć porównać otrzymany ciąg identyfikacyjny z publicznym ciągiem agenta SNMP, jeśli żądanie jest typu GET lub do prywatnego ciągu agenta SNMP, jeśli żądanie jest typem zestawu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-283">It is intended for use with the username callback where the SNMPv1 or SNMPv2 application will want to compare the received community string to the SNMP Agent public string if the request is a GET type, or to the SNMP Agent private string if the request is a SET type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-284">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-284">Input Parameters</span></span>

- <span data-ttu-id="aa55c-285">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-285">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-286">**is_get_type** Wskaźnik do stanu typu żądania:</span><span class="sxs-lookup"><span data-stu-id="aa55c-286">**is_get_type** Pointer to request type status:</span></span>  
<span data-ttu-id="aa55c-287">NX_TRUE Jeśli typ pobrania</span><span class="sxs-lookup"><span data-stu-id="aa55c-287">NX_TRUE if GET type</span></span>  
<span data-ttu-id="aa55c-288">NX_FALSE Jeśli typ zestawu</span><span class="sxs-lookup"><span data-stu-id="aa55c-288">NX_FALSE if SET type</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-289">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-289">Return Values</span></span>

- <span data-ttu-id="aa55c-290">**NX_SUCCESS** (0X00) pomyślnie zwrócił typ</span><span class="sxs-lookup"><span data-stu-id="aa55c-290">**NX_SUCCESS** (0x00) Successfully returned type</span></span>
- <span data-ttu-id="aa55c-291">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-291">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-292">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-292">Allowed From</span></span>

<span data-ttu-id="aa55c-293">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-293">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-294">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-294">Example</span></span>

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a><span data-ttu-id="aa55c-295">nx_snmp_agent_context_engine_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-295">nx_snmp_agent_context_engine_set</span></span>
<span data-ttu-id="aa55c-296">Ustaw aparat kontekstu (tylko protokół SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="aa55c-296">Set context engine (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-297">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-297">Prototype</span></span>

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a><span data-ttu-id="aa55c-298">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-298">Description</span></span>

<span data-ttu-id="aa55c-299">Ta usługa ustawia aparat kontekstu agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-299">This service sets the context engine of the SNMP Agent.</span></span> <span data-ttu-id="aa55c-300">Ma to zastosowanie tylko w przypadku przetwarzania SNMPv3.</span><span class="sxs-lookup"><span data-stu-id="aa55c-300">It is only applicable for SNMPv3 processing.</span></span> <span data-ttu-id="aa55c-301">Należy to wywołać przed utworzeniem kluczy zabezpieczeń, jeśli aplikacja korzysta z uwierzytelniania i szyfrowania, ponieważ w procesie tworzenia klucza jest używany identyfikator aparatu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-301">This should be called before creating security keys if the application is using authentication and encryption, since the context engine ID is used in the key creation process.</span></span> <span data-ttu-id="aa55c-302">Jeśli nie, NetX Duo SNMP zapewnia domyślny identyfikator aparatu kontekstu w górnej części *nxd_snmp. c:*</span><span class="sxs-lookup"><span data-stu-id="aa55c-302">If not, NetX Duo SNMP provides a default context engine id at the top of *nxd_snmp.c:*</span></span>

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a><span data-ttu-id="aa55c-303">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-303">Input Parameters</span></span>

- <span data-ttu-id="aa55c-304">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-304">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-305">**context_engine** Wskaźnik na ciąg aparatu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-305">**context_engine** Pointer to the context engine string.</span></span>
- <span data-ttu-id="aa55c-306">**context_engine_size** Rozmiar ciągu aparatu kontekstu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-306">**context_engine_size** Size of context engine string.</span></span> <span data-ttu-id="aa55c-307">Należy zauważyć, że maksymalna liczba bajtów w aparacie kontekstu jest definiowana przez NX_SNMP_MAX_CONTEXT_STRING.</span><span class="sxs-lookup"><span data-stu-id="aa55c-307">Note that the maximum number of bytes in a context engine is defined by NX_SNMP_MAX_CONTEXT_STRING.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-308">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-308">Return Values</span></span>

- <span data-ttu-id="aa55c-309">**NX_SUCCESS** (0x00) zestaw aparatów kontekstu SNMP zakończony pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="aa55c-309">**NX_SUCCESS** (0x00) Successful SNMP context engine set.</span></span>
- <span data-ttu-id="aa55c-310">**NX_NOT_ENABLED** (0X14) SNMPv3 nie jest włączona</span><span class="sxs-lookup"><span data-stu-id="aa55c-310">**NX_NOT_ENABLED** (0x14) SNMPv3 is not enabled</span></span>
- <span data-ttu-id="aa55c-311">Błąd rozmiaru aparatu **NX_SNMP_ERROR** (0x100).</span><span class="sxs-lookup"><span data-stu-id="aa55c-311">**NX_SNMP_ERROR** (0x100) Context engine size error.</span></span>
- <span data-ttu-id="aa55c-312">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-312">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-313">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-313">Allowed From</span></span>

<span data-ttu-id="aa55c-314">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-314">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-315">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-315">Example</span></span>

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a><span data-ttu-id="aa55c-316">nx_snmp_agent_context_name_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-316">nx_snmp_agent_context_name_set</span></span>
<span data-ttu-id="aa55c-317">Ustaw nazwę kontekstu (tylko protokół SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="aa55c-317">Set context name (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-318">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-318">Prototype</span></span>

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a><span data-ttu-id="aa55c-319">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-319">Description</span></span>

<span data-ttu-id="aa55c-320">Ta usługa ustawia nazwę kontekstu agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-320">This service sets the context name of the SNMP Agent.</span></span> <span data-ttu-id="aa55c-321">Ma to zastosowanie tylko w przypadku przetwarzania SNMPv3.</span><span class="sxs-lookup"><span data-stu-id="aa55c-321">It is only applicable for SNMPv3 processing.</span></span> <span data-ttu-id="aa55c-322">Jeśli nie zostanie wywołana, Agent SNMP NetX Duo pozostawi pustej nazwy kontekstu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-322">If not called, NetX Duo SNMP Agent will leave the context name blank.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-323">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-323">Input Parameters</span></span>

- <span data-ttu-id="aa55c-324">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-324">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-325">**context_name** Wskaźnik na ciąg nazwy kontekstu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-325">**context_name** Pointer to the context name string.</span></span>
- <span data-ttu-id="aa55c-326">**context_name_size** Rozmiar ciągu nazwy kontekstu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-326">**context_name_size** Size of context name string.</span></span> <span data-ttu-id="aa55c-327">Należy zauważyć, że maksymalna liczba bajtów w nazwie kontekstu jest definiowana przez NX_SNMP_MAX_CONTEXT_STRING.</span><span class="sxs-lookup"><span data-stu-id="aa55c-327">Note that the maximum number of bytes in a context name is defined by NX_SNMP_MAX_CONTEXT_STRING.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-328">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-328">Return Values</span></span>

- <span data-ttu-id="aa55c-329">**NX_SUCCESS** (0x00) pomyślna Nazwa kontekstu SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-329">**NX_SUCCESS** (0x00) Successful SNMP context name set.</span></span>
- <span data-ttu-id="aa55c-330">Błąd rozmiaru nazwy kontekstu **NX_SNMP_ERROR** (0x100).</span><span class="sxs-lookup"><span data-stu-id="aa55c-330">**NX_SNMP_ERROR** (0x100) Context name size error.</span></span>
- <span data-ttu-id="aa55c-331">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-331">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-332">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-332">Allowed From</span></span>

<span data-ttu-id="aa55c-333">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-333">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-334">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-334">Example</span></span>

```c
/* Set the context name for my_agent.  */
status =  nx_snmp_agent_context_name_set(&my_agent, “my_context_name”, 15);


/* If status is NX_SUCCESS the context name has been set.  */
```

## <a name="nx_snmp_agent_create"></a><span data-ttu-id="aa55c-335">nx_snmp_agent_create</span><span class="sxs-lookup"><span data-stu-id="aa55c-335">nx_snmp_agent_create</span></span>
<span data-ttu-id="aa55c-336">Utwórz agenta SNMP</span><span class="sxs-lookup"><span data-stu-id="aa55c-336">Create SNMP agent</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-337">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-337">Prototype</span></span>

```c
UINT nx_snmp_agent_create(NX_SNMP_AGENT *agent_ptr, 
      CHAR *snmp_agent_name, NX_IP *ip_ptr, VOID *stack_ptr, 
      ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*snmp_agent_username_process)(struct NX_SNMP_AGENT_STRUCT 
                                    *agent_ptr, UCHAR *username),
      UINT (*snmp_agent_get_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_getnext_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_set_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data));
```
### <a name="description"></a><span data-ttu-id="aa55c-338">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-338">Description</span></span>

<span data-ttu-id="aa55c-339">Ta usługa tworzy agenta SNMP dla określonego wystąpienia IP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-339">This service creates a SNMP Agent on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-340">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-340">Input Parameters</span></span>

- <span data-ttu-id="aa55c-341">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-341">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-342">**snmp_agent_name** Wskaźnik do ciągu nazwy agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-342">**snmp_agent_name** Pointer to the SNMP Agent name string.</span></span>
- <span data-ttu-id="aa55c-343">**ip_ptr** Wskaźnik na wystąpienie adresu IP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-343">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="aa55c-344">**stack_ptr** Wskaźnik do wskaźnika stosu wątku agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-344">**stack_ptr** Pointer to SNMP Agent thread stack pointer.</span></span>
- <span data-ttu-id="aa55c-345">**stack_size** Rozmiar stosu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="aa55c-345">**stack_size** Stack size in bytes.</span></span>
- <span data-ttu-id="aa55c-346">**pool_ptr** Wskaźnik domyślnej puli pakietów dla tego agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-346">**pool_ptr** Pointer the default packet pool for this SNMP Agent.</span></span>
- <span data-ttu-id="aa55c-347">**snmp_agent_username_process** Wskaźnik funkcji do procedury obsługi nazwy użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-347">**snmp_agent_username_process** Function pointer to application’s username handling routine.</span></span>
- <span data-ttu-id="aa55c-348">**snmp_agent_get_process** Wskaźnik funkcji do procedury obsługi żądania GET.</span><span class="sxs-lookup"><span data-stu-id="aa55c-348">**snmp_agent_get_process** Function pointer to application’s GET request handling routine.</span></span>
- <span data-ttu-id="aa55c-349">**snmp_agent_getnext_process** Wskaźnik funkcji do procedury obsługi GetNext Request dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-349">**snmp_agent_getnext_process** Function pointer to application’s GETNEXT request handling routine.</span></span>
- <span data-ttu-id="aa55c-350">**snmp_agent_set_process** Wskaźnik funkcji do procedury obsługi żądania zestawu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-350">**snmp_agent_set_process** Function pointer to application’s SET request handling routine.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-351">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-351">Return Values</span></span>

- <span data-ttu-id="aa55c-352">**NX_SUCCESS** (0X00) pomyślne utworzenie agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-352">**NX_SUCCESS** (0x00) Successful SNMP Agent create.</span></span>
- <span data-ttu-id="aa55c-353">**NX_SNMP_ERROR** (0x100) wystąpił błąd podczas tworzenia agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-353">**NX_SNMP_ERROR** (0x100) SNMP Agent create error.</span></span>
- <span data-ttu-id="aa55c-354">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-354">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-355">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-355">Allowed From</span></span>

<span data-ttu-id="aa55c-356">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-356">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-357">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-357">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Create the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_create(&my_agent, "My SNMP Agent", &ip_0, stack_start_ptr,
                4096, &pool_0, my_username_processing, my_get_processing, 
                my_getnext_processing, my_set_processing);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been created.  */
```

## <a name="nx_snmp_agent_current_version_get"></a><span data-ttu-id="aa55c-358">nx_snmp_agent_current_version_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-358">nx_snmp_agent_current_version_get</span></span>
<span data-ttu-id="aa55c-359">Pobierz wersję pakietu SNMP</span><span class="sxs-lookup"><span data-stu-id="aa55c-359">Get the SNMP packet version</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-360">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-360">Prototype</span></span>

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a><span data-ttu-id="aa55c-361">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-361">Description</span></span>

<span data-ttu-id="aa55c-362">Ta usługa Pobiera wersję protokołu SNMP przeanalizowane z ostatniego odebranego pakietu SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-362">This service retrieves the SNMP version parsed from the most recent SNMP packet received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-363">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-363">Input Parameters</span></span>

- <span data-ttu-id="aa55c-364">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-364">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-365">**wersja** Wskaźnik do wersji SNMP przeanalizowanej z odebranego pakietu SNMP</span><span class="sxs-lookup"><span data-stu-id="aa55c-365">**version** Pointer to the SNMP version parsed from received SNMP packet</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-366">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-366">Return Values</span></span>

- <span data-ttu-id="aa55c-367">**NX_SUCCESS** (0X00) pomyślne pobieranie wersji SNMP</span><span class="sxs-lookup"><span data-stu-id="aa55c-367">**NX_SUCCESS** (0x00) Successful SNMP version get</span></span>
- <span data-ttu-id="aa55c-368">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="aa55c-368">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-369">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-369">Allowed From</span></span>

<span data-ttu-id="aa55c-370">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-370">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-371">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-371">Example</span></span>

```c
UINT          snmp_version;
NX_SNMP_AGENT my_agent;

/* Get the version of the last received SNMP packet. */
status =  nx_snmp_agent_current_version_get (&my_agent, &snmp_version);


/* If status is NX_SUCCESS, snmp_version contains 
   the received packet SNMP version.  */
```

## <a name="nx_snmp_agent_private_string_test"></a><span data-ttu-id="aa55c-372">nx_snmp_agent_private_string_test</span><span class="sxs-lookup"><span data-stu-id="aa55c-372">nx_snmp_agent_private_string_test</span></span>
<span data-ttu-id="aa55c-373">Sprawdź, czy ciąg prywatny jest zgodny z prywatnym ciągiem agenta</span><span class="sxs-lookup"><span data-stu-id="aa55c-373">Verify private string matches Agent private string</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-374">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-374">Prototype</span></span>

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a><span data-ttu-id="aa55c-375">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-375">Description</span></span>

<span data-ttu-id="aa55c-376">Ta usługa porównuje ciąg identyfikacyjny zakończony zerem o wartości null z prywatnym ciągiem agenta SNMP i wskazuje, czy są one zgodne.</span><span class="sxs-lookup"><span data-stu-id="aa55c-376">This service compares the null terminated input community string with the SNMP agent private string and indicates if they match.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-377">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-377">Input Parameters</span></span>

- <span data-ttu-id="aa55c-378">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-378">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-379">**community_string** Wskaźnik do ciągu do porównania</span><span class="sxs-lookup"><span data-stu-id="aa55c-379">**community_string** Pointer to string to compare</span></span>
- <span data-ttu-id="aa55c-380">**is_private** Wskaźnik do wyniku porównania</span><span class="sxs-lookup"><span data-stu-id="aa55c-380">**is_private** Pointer to result of comparison</span></span>  
<span data-ttu-id="aa55c-381">Dopasowania ciągu NX_TRUE</span><span class="sxs-lookup"><span data-stu-id="aa55c-381">NX_TRUE - string matches</span></span>  
<span data-ttu-id="aa55c-382">NX_FALSE — ciąg nie jest zgodny</span><span class="sxs-lookup"><span data-stu-id="aa55c-382">NX_FALSE - string does not match</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-383">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-383">Return Values</span></span>

- <span data-ttu-id="aa55c-384">Pomyślne porównanie **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="aa55c-384">**NX_SUCCESS** (0x00) Successful comparison</span></span>
- <span data-ttu-id="aa55c-385">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="aa55c-385">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-386">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-386">Allowed From</span></span>

<span data-ttu-id="aa55c-387">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-387">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-388">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-388">Example</span></span>

```c
UINT        is_private;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;

/* Determine if the community string matches the agent private string */
status =  nx_snmp_agent_private_string_test(&my_agent, community_string_ptr,  
                                            &is_private);


/* If status is NX_SUCCESS, is_private will indicate if there is a match. 
   If is_private is NX_TRUE, they match.  */
```

## <a name="nx_snmp_agent_public_string_test"></a><span data-ttu-id="aa55c-389">nx_snmp_agent_public_string_test</span><span class="sxs-lookup"><span data-stu-id="aa55c-389">nx_snmp_agent_public_string_test</span></span>
<span data-ttu-id="aa55c-390">Sprawdź, czy otrzymany ciąg publiczny jest zgodny z publicznym ciągiem agenta</span><span class="sxs-lookup"><span data-stu-id="aa55c-390">Verify received public string matches Agent’s public string</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-391">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-391">Prototype</span></span>

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a><span data-ttu-id="aa55c-392">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-392">Description</span></span>

<span data-ttu-id="aa55c-393">Ta usługa porównuje ciąg identyfikacyjny zakończony zerem o wartości null z publicznym ciągiem agenta SNMP i wskazuje, czy są one zgodne.</span><span class="sxs-lookup"><span data-stu-id="aa55c-393">This service compares a null terminated input community string with the SNMP agent public string and indicates if they match.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-394">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-394">Input Parameters</span></span>

- <span data-ttu-id="aa55c-395">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-395">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-396">**community_string** Wskaźnik do ciągu do porównania</span><span class="sxs-lookup"><span data-stu-id="aa55c-396">**community_string** Pointer to string to compare</span></span>
- <span data-ttu-id="aa55c-397">**is_public** Wskaźnik do wyniku porównania</span><span class="sxs-lookup"><span data-stu-id="aa55c-397">**is_public** Pointer to result of comparison</span></span>  
<span data-ttu-id="aa55c-398">Dopasowania ciągu NX_TRUE</span><span class="sxs-lookup"><span data-stu-id="aa55c-398">NX_TRUE - string matches</span></span>  
<span data-ttu-id="aa55c-399">NX_FALSE — ciąg nie jest zgodny</span><span class="sxs-lookup"><span data-stu-id="aa55c-399">NX_FALSE - string does not match</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-400">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-400">Return Values</span></span>

- <span data-ttu-id="aa55c-401">Pomyślne porównanie **NX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="aa55c-401">**NX_SUCCESS** (0x00) Successful comparison</span></span>
- <span data-ttu-id="aa55c-402">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="aa55c-402">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-403">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-403">Allowed From</span></span>

<span data-ttu-id="aa55c-404">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-404">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-405">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-405">Example</span></span>

```c
UINT        is_public;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;


/* Determine if the community string matches the agent public string */
status =  nx_snmp_agent_public_string_test(&my_agent, community_string_ptr,  
                                           &is_public);


/* If status is NX_SUCCESS, is_public will indicate if there is a match. 
   If is_public is true they match.  */
```

## <a name="nx_snmp_agent_version_set"></a><span data-ttu-id="aa55c-406">nx_snmp_agent_version_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-406">nx_snmp_agent_version_set</span></span>
<span data-ttu-id="aa55c-407">Ustaw stan agenta SNMP dla każdej wersji SNMP</span><span class="sxs-lookup"><span data-stu-id="aa55c-407">Set the SNMP agent status for each SNMP version</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-408">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-408">Prototype</span></span>

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a><span data-ttu-id="aa55c-409">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-409">Description</span></span>

<span data-ttu-id="aa55c-410">Ta usługa ustawia stan (włączony/wyłączony) dla każdego z wersji SNMP, v1, v2 i V3 w agencie SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-410">This service sets the status (enabled/disabled) for each of the SNMP versions, V1, V2 and V3 on the SNMP agent.</span></span> <span data-ttu-id="aa55c-411">Należy pamiętać, że opcje konfigurowane przez użytkownika, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 i NX_SNMP_DISABLE_V3, przesłonią te ustawienia czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="aa55c-411">Note that the user configurable options, NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2, and NX_SNMP_DISABLE_V3, will override these run time settings.</span></span> <span data-ttu-id="aa55c-412">Domyślnie Agent SNMP jest włączony dla wszystkich trzech wersji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-412">By default, the SNMP agent is enabled for all three versions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-413">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-413">Input Parameters</span></span>

- <span data-ttu-id="aa55c-414">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-414">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-415">**enabled_v1** Ustawia stan włączenia protokołu SNMP v1 na Włącz/Wyłącz.</span><span class="sxs-lookup"><span data-stu-id="aa55c-415">**enabled_v1** Sets enabled status for SNMP V1 to on/off.</span></span>
- <span data-ttu-id="aa55c-416">**enabled_v2** Ustawia stan włączenia protokołu SNMP V2 na Włącz/Wyłącz.</span><span class="sxs-lookup"><span data-stu-id="aa55c-416">**enabled_v2** Sets enabled status for SNMP V2 to on/off.</span></span>
- <span data-ttu-id="aa55c-417">**enabled_v3** Ustawia stan włączenia protokołu SNMP V3 na Włącz/Wyłącz.</span><span class="sxs-lookup"><span data-stu-id="aa55c-417">**enabled_v3** Sets enabled status for SNMP V3 to on/off.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-418">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-418">Return Values</span></span>

- <span data-ttu-id="aa55c-419">**NX_SUCCESS** (0X00) pomyślne Ustawianie wersji SNMP</span><span class="sxs-lookup"><span data-stu-id="aa55c-419">**NX_SUCCESS** (0x00) Successful SNMP version set</span></span>
- <span data-ttu-id="aa55c-420">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="aa55c-420">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-421">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-421">Allowed From</span></span>

<span data-ttu-id="aa55c-422">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-422">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-423">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-423">Example</span></span>

```c
UINT          v1_on = NX_TRUE;
UINT          v2_on = NX_TRUE;
UINT          v3_on = NX_FALSE;

NX_SNMP_AGENT my_agent;

/* Enable/Disable each SNMP protocol (version) for the SNMP Agent) */
status =  nx_snmp_agent_version_set(&my_agent, v1_on, v2_on, v3_on);


/* If status is NX_SUCCESS, my_agent is enabled only for V1 and V2 assuming 
   NX_SNMP_DISABLE_V1 and NX_SNMP_DISABLE_V2 are not defined. */
```

## <a name="nx_snmp_agent_private_string_set"></a><span data-ttu-id="aa55c-424">nx_snmp_agent_private_string_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-424">nx_snmp_agent_private_string_set</span></span>
<span data-ttu-id="aa55c-425">Ustaw ciąg prywatny agenta SNMP</span><span class="sxs-lookup"><span data-stu-id="aa55c-425">Set the SNMP agent private string</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-426">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-426">Prototype</span></span>

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a><span data-ttu-id="aa55c-427">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-427">Description</span></span>

<span data-ttu-id="aa55c-428">Ta usługa ustawia ciąg społeczności prywatnej agenta SNMP z ciągiem zakończonym zerem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="aa55c-428">This service sets the SNMP agent private community string with the input null terminated string.</span></span> <span data-ttu-id="aa55c-429">Wartość domyślna to NULL (bez prywatnego zestawu parametrów), w taki sposób, że żaden pakiet SNMP otrzymany z "prywatnym" ciągiem Wspólnoty nie zostanie zaakceptowany przez agenta SNMP na potrzeby dostępu do odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-429">The default value is NULL (no private string set), such that any SNMP packet received with a “private” community string will not be accepted by the SNMP agent for read/write access.</span></span> <span data-ttu-id="aa55c-430">Ciąg wejściowy musi być mniejszy niż lub równy użytkownikowi konfigurowalnemu NX_SNMP_MAX_USER_NAME-1 (aby można było pozostawić miejsce na zakończenie o wartości null).</span><span class="sxs-lookup"><span data-stu-id="aa55c-430">The input string must be less than or equal to the user configurable NX_SNMP_MAX_USER_NAME-1 (to allow room for null termination) size.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-431">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-431">Input Parameters</span></span>

- <span data-ttu-id="aa55c-432">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-432">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-433">**community_string** Wskaźnik do prywatnego ciągu do przypisania</span><span class="sxs-lookup"><span data-stu-id="aa55c-433">**community_string** Pointer to the private string to assign</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-434">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-434">Return Values</span></span>

- <span data-ttu-id="aa55c-435">**NX_SUCCESS** (0X00) pomyślnie ustawił ciąg prywatny</span><span class="sxs-lookup"><span data-stu-id="aa55c-435">**NX_SUCCESS** (0x00) Successfully set private string</span></span>
- <span data-ttu-id="aa55c-436">Rozmiar ciągu **NX_SNMP_ERROR_TOOBIG** (0x01) jest zbyt duży</span><span class="sxs-lookup"><span data-stu-id="aa55c-436">**NX_SNMP_ERROR_TOOBIG** (0x01) String size too large</span></span> 
- <span data-ttu-id="aa55c-437">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="aa55c-437">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-438">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-438">Allowed From</span></span>

<span data-ttu-id="aa55c-439">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-439">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-440">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-440">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s private community string */
status =  nx_snmp_agent_private_string_set(&my_agent, “private”));


/* If status is NX_SUCCESS, the SNMP agent private string is set.  */
```

## <a name="nx_snmp_agent_public_string_set"></a><span data-ttu-id="aa55c-441">nx_snmp_agent_public_string_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-441">nx_snmp_agent_public_string_set</span></span>
<span data-ttu-id="aa55c-442">Ustawianie ciągu publicznego agenta SNMP</span><span class="sxs-lookup"><span data-stu-id="aa55c-442">Set the SNMP agent public string</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-443">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-443">Prototype</span></span>

```c
UINT nx_snmp_agent_public_string_set(NX_SNMP_AGENT *agent_ptr, 
                                     UCHAR *community_string);
```

### <a name="description"></a><span data-ttu-id="aa55c-444">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-444">Description</span></span>

<span data-ttu-id="aa55c-445">Ta usługa ustawia ciąg społeczności publicznej agenta SNMP z ciągiem zakończonym zerem o wartości null.</span><span class="sxs-lookup"><span data-stu-id="aa55c-445">This service sets the SNMP agent public community string with the input null terminated string.</span></span> <span data-ttu-id="aa55c-446">Ciąg identyfikacyjny nie może być mniejszy niż lub równy użytkownikowi konfigurowalnemu NX_SNMP_MAX_USER_NAME-1 (aby można było zwolnić miejsce na zakończenie o wartości null).</span><span class="sxs-lookup"><span data-stu-id="aa55c-446">The community string must be less than or equal to the user configurable NX_SNMP_MAX_USER_NAME-1 (to allow room for null termination) size.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-447">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-447">Input Parameters</span></span>

- <span data-ttu-id="aa55c-448">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-448">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-449">**community_string** Wskaźnik na ciąg publiczny do przypisania</span><span class="sxs-lookup"><span data-stu-id="aa55c-449">**community_string** Pointer to the public string to assign</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-450">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-450">Return Values</span></span>

- <span data-ttu-id="aa55c-451">**NX_SUCCESS** (0X00) pomyślnie ustawił ciąg publiczny</span><span class="sxs-lookup"><span data-stu-id="aa55c-451">**NX_SUCCESS** (0x00) Successfully set public string</span></span>
- <span data-ttu-id="aa55c-452">Rozmiar ciągu **NX_SNMP_ERROR_TOOBIG** (0x01) jest zbyt duży</span><span class="sxs-lookup"><span data-stu-id="aa55c-452">**NX_SNMP_ERROR_TOOBIG** (0x01) String size too large</span></span>
- <span data-ttu-id="aa55c-453">**NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika</span><span class="sxs-lookup"><span data-stu-id="aa55c-453">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-454">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-454">Allowed From</span></span>

<span data-ttu-id="aa55c-455">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-455">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-456">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-456">Example</span></span>

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s public string. */
nx_snmp_agent_public_string_set(&my_agent, “my_public”));


/* If status is NX_SUCCESS, the SNMP agent public string is set.  */
```

## <a name="nx_snmp_agent_delete"></a><span data-ttu-id="aa55c-457">nx_snmp_agent_delete</span><span class="sxs-lookup"><span data-stu-id="aa55c-457">nx_snmp_agent_delete</span></span>
<span data-ttu-id="aa55c-458">Usuń agenta SNMP</span><span class="sxs-lookup"><span data-stu-id="aa55c-458">Delete SNMP agent</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-459">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-459">Prototype</span></span>

```C
UINT nx_snmp_agent_delete(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="aa55c-460">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-460">Description</span></span>

<span data-ttu-id="aa55c-461">Ta usługa usuwa wcześniej utworzonego agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-461">This service deletes a previously created SNMP Agent.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-462">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-462">Input Parameters</span></span>

- <span data-ttu-id="aa55c-463">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-463">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-464">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-464">Return Values</span></span>

- <span data-ttu-id="aa55c-465">**NX_SUCCESS** (0X00) pomyślne usunięcie agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-465">**NX_SUCCESS** (0x00) Successful SNMP Agent delete.</span></span>
- <span data-ttu-id="aa55c-466">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-466">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-467">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-467">Allowed From</span></span>

<span data-ttu-id="aa55c-468">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-468">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-469">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-469">Example</span></span>

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a><span data-ttu-id="aa55c-470">nx_snmp_agent_set_interface</span><span class="sxs-lookup"><span data-stu-id="aa55c-470">nx_snmp_agent_set_interface</span></span>
<span data-ttu-id="aa55c-471">Ustaw interfejs sieciowy agenta SNMP</span><span class="sxs-lookup"><span data-stu-id="aa55c-471">Set the SNMP agent network interface</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-472">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-472">Prototype</span></span>

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a><span data-ttu-id="aa55c-473">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-473">Description</span></span>

<span data-ttu-id="aa55c-474">Ta usługa ustawia interfejs sieciowy SNMP dla agenta SNMP określony przez indeks interfejsu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-474">This service sets the SNMP network interface for the SNMP Agent as specified by the input interface index.</span></span> <span data-ttu-id="aa55c-475">Jest to przydatne tylko w przypadku aplikacji hosta SNMP z NetX Duo 5,6 lub nowszymi, które obsługują wiele interfejsów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="aa55c-475">This is only useful for SNMP host applications with NetX Duo 5.6 or higher which support multiple network interfaces.</span></span> <span data-ttu-id="aa55c-476">Wartość domyślna, jeśli nie zostanie określona przez hosta, wynosi zero dla interfejsu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-476">The default value if not specified by the host is zero, for the primary interface.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-477">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-477">Input Parameters</span></span>

- <span data-ttu-id="aa55c-478">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-478">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-479">**If_index** Indeks określający interfejs SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-479">**If_index** Index specifying the SNMP interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-480">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-480">Return Values</span></span>

- <span data-ttu-id="aa55c-481">**NX_SUCCESS** (0X00) pomyślnie ustawiono interfejs SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-481">**NX_SUCCESS** (0x00) Successful SNMP interface set.</span></span>
- <span data-ttu-id="aa55c-482">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-482">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-483">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-483">Allowed From</span></span>

<span data-ttu-id="aa55c-484">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-484">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-485">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-485">Example</span></span>

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a><span data-ttu-id="aa55c-486">nx_snmp_agent_md5_key_create</span><span class="sxs-lookup"><span data-stu-id="aa55c-486">nx_snmp_agent_md5_key_create</span></span>
<span data-ttu-id="aa55c-487">Utwórz klucz MD5 (tylko protokół SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="aa55c-487">Create md5 key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-488">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-488">Prototype</span></span>

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a><span data-ttu-id="aa55c-489">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-489">Description</span></span>

<span data-ttu-id="aa55c-490">Ta usługa tworzy klucz MD5, który może służyć do uwierzytelniania i szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="aa55c-490">This service creates a MD5 key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="aa55c-491">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="aa55c-491">This service is deprecated.</span></span> <span data-ttu-id="aa55c-492">Deweloperzy są zachęcani do migracji do *nx_snmp_agent_md5_key_create_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="aa55c-492">Developers are encouraged to migrate to *nx_snmp_agent_md5_key_create_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-493">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-493">Input Parameters</span></span>

- <span data-ttu-id="aa55c-494">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-494">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-495">**hasło** Wskaźnik na ciąg hasła.</span><span class="sxs-lookup"><span data-stu-id="aa55c-495">**password** Pointer to password string.</span></span>
- <span data-ttu-id="aa55c-496">**destination_key** Wskaźnik do struktury danych klucza SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-496">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-497">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-497">Return Values</span></span>

- <span data-ttu-id="aa55c-498">Pomyślnie utworzono klucz **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="aa55c-498">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="aa55c-499">Nie włączono zabezpieczeń **NX_NOT_ENABLED** (0x14).</span><span class="sxs-lookup"><span data-stu-id="aa55c-499">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="aa55c-500">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-500">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-501">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-501">Allowed From</span></span>

<span data-ttu-id="aa55c-502">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-502">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-503">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-503">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a><span data-ttu-id="aa55c-504">nx_snmp_agent_md5_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="aa55c-504">nx_snmp_agent_md5_key_create_extended</span></span>
<span data-ttu-id="aa55c-505">Utwórz klucz MD5 (tylko protokół SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="aa55c-505">Create md5 key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-506">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-506">Prototype</span></span>

```c
UINT nx_snmp_agent_md5_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY 
                                           *destination_key);
```
### <a name="description"></a><span data-ttu-id="aa55c-507">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-507">Description</span></span>

<span data-ttu-id="aa55c-508">Ta usługa tworzy klucz MD5, który może służyć do uwierzytelniania i szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="aa55c-508">This service creates a MD5 key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="aa55c-509">Ta usługa zastępuje *nx_snmp_agent_md5_key_create ().*</span><span class="sxs-lookup"><span data-stu-id="aa55c-509">This service replaces *nx_snmp_agent_md5_key_create().*</span></span> <span data-ttu-id="aa55c-510">Ta wersja wymaga, aby obiekt wywołujący dostarczał długość hasła.</span><span class="sxs-lookup"><span data-stu-id="aa55c-510">This version requires caller to supply password length.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-511">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-511">Input Parameters</span></span>

- <span data-ttu-id="aa55c-512">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-512">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-513">**hasło** Wskaźnik na ciąg hasła.</span><span class="sxs-lookup"><span data-stu-id="aa55c-513">**password** Pointer to password string.</span></span>
- <span data-ttu-id="aa55c-514">**password_length** Długość ciągu hasła.</span><span class="sxs-lookup"><span data-stu-id="aa55c-514">**password_length** Length of password string.</span></span>
- <span data-ttu-id="aa55c-515">**destination_key** Wskaźnik do struktury danych klucza SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-515">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-516">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-516">Return Values</span></span>

- <span data-ttu-id="aa55c-517">Pomyślnie utworzono klucz **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="aa55c-517">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="aa55c-518">Nie włączono zabezpieczeń **NX_NOT_ENABLED** (0x14).</span><span class="sxs-lookup"><span data-stu-id="aa55c-518">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="aa55c-519">**NX_SNMP_FAILED** (0X102) SNMP nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="aa55c-519">**NX_SNMP_FAILED** (0x102) SNMP failed.</span></span>
- <span data-ttu-id="aa55c-520">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-520">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-521">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-521">Allowed From</span></span>

<span data-ttu-id="aa55c-522">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-522">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-523">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-523">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a><span data-ttu-id="aa55c-524">nx_snmp_agent_priv_trap_key_use</span><span class="sxs-lookup"><span data-stu-id="aa55c-524">nx_snmp_agent_priv_trap_key_use</span></span>
<span data-ttu-id="aa55c-525">Określ klucz szyfrowania dla komunikatów pułapki</span><span class="sxs-lookup"><span data-stu-id="aa55c-525">Specify encryption key for trap messages</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-526">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-526">Prototype</span></span>

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a><span data-ttu-id="aa55c-527">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-527">Description</span></span>

<span data-ttu-id="aa55c-528">Ta usługa określa, że wcześniej utworzony klucz prywatności ma być używany do szyfrowania i odszyfrowywania komunikatów pułapki SNMPv3.</span><span class="sxs-lookup"><span data-stu-id="aa55c-528">This service specifies that a previously created privacy key is to be used for encryption and decryption of SNMPv3 trap messages.</span></span>

> [!NOTE]
> <span data-ttu-id="aa55c-529">*Należy wcześniej utworzyć klucz authentictation. W przypadku protokołu SNMP v3 (szyfrowanie) wymagane jest uwierzytelnienie. Aby uzyskać szczegółowe informacje, zobacz nx_snmp_agent_auth_trap_key_use.*</span><span class="sxs-lookup"><span data-stu-id="aa55c-529">*An authentictation key must be previously created. SNMP v3 privacy (encryption) requires authentication. See nx_snmp_agent_auth_trap_key_use for details.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-530">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-530">Input Parameters</span></span>

- <span data-ttu-id="aa55c-531">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-531">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-532">**klucz** Wskaźnik do wcześniej utworzonego klucza.</span><span class="sxs-lookup"><span data-stu-id="aa55c-532">**key** Pointer to previously create key.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-533">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-533">Return Values</span></span>

- <span data-ttu-id="aa55c-534">**NX_SUCCESS** (0X00) pomyślnie ustawiono klucz prywatności.</span><span class="sxs-lookup"><span data-stu-id="aa55c-534">**NX_SUCCESS** (0x00) Successful privacy key set.</span></span>
- <span data-ttu-id="aa55c-535">Nie włączono zabezpieczeń **NX_NOT_ENABLED** (0x14).</span><span class="sxs-lookup"><span data-stu-id="aa55c-535">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="aa55c-536">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-536">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-537">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-537">Allowed From</span></span>

<span data-ttu-id="aa55c-538">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-538">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-539">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-539">Example</span></span>

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a><span data-ttu-id="aa55c-540">nx_snmp_agent_privacy_key_use</span><span class="sxs-lookup"><span data-stu-id="aa55c-540">nx_snmp_agent_privacy_key_use</span></span>
<span data-ttu-id="aa55c-541">Określ klucz szyfrowania dla komunikatów odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="aa55c-541">Specify encryption key for response messages</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-542">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-542">Prototype</span></span>

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a><span data-ttu-id="aa55c-543">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-543">Description</span></span>

<span data-ttu-id="aa55c-544">Ta usługa określa, że utworzony wcześniej klucz ma być używany do szyfrowania i odszyfrowywania komunikatów odpowiedzi SNMPv3.</span><span class="sxs-lookup"><span data-stu-id="aa55c-544">This service specifies that the previously created key is to be used for encryption and decryption of SNMPv3 response messages.</span></span>

> [!NOTE]
> <span data-ttu-id="aa55c-545">*Należy wcześniej określić klucz uwierzytelniania. Szyfrowanie SNMP v3 wymaga również utworzenia klucza uwierzytelniania. Aby uzyskać szczegółowe informacje, zobacz nx_snmp_agent_authentiation_key_use.*</span><span class="sxs-lookup"><span data-stu-id="aa55c-545">*An authentication key must have previously been specified. SNMP v3 encryption requires creation of an authentication key as well. See nx_snmp_agent_authentiation_key_use for details.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-546">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-546">Input Parameters</span></span>

- <span data-ttu-id="aa55c-547">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-547">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-548">**klucz** Wskaźnik do wcześniej utworzonego klucza.</span><span class="sxs-lookup"><span data-stu-id="aa55c-548">**key** Pointer to previously create key.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-549">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-549">Return Values</span></span>

- <span data-ttu-id="aa55c-550">**NX_SUCCESS** (0X00) pomyślnie ustawiono klucz prywatności.</span><span class="sxs-lookup"><span data-stu-id="aa55c-550">**NX_SUCCESS** (0x00) Successful privacy key set.</span></span>
- <span data-ttu-id="aa55c-551">Nie włączono zabezpieczeń **NX_NOT_ENABLED** (0x14).</span><span class="sxs-lookup"><span data-stu-id="aa55c-551">**NX_NOT_ENABLED** (0x14) Security not enabled.</span></span>
- <span data-ttu-id="aa55c-552">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-552">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-553">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-553">Allowed From</span></span>

<span data-ttu-id="aa55c-554">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-554">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-555">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-555">Example</span></span>

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_sha_key_create"></a><span data-ttu-id="aa55c-556">nx_snmp_agent_sha_key_create</span><span class="sxs-lookup"><span data-stu-id="aa55c-556">nx_snmp_agent_sha_key_create</span></span>
<span data-ttu-id="aa55c-557">Utwórz klucz SHA (tylko protokół SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="aa55c-557">Create SHA key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-558">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-558">Prototype</span></span>

```c
UINT nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY  
                                  *destination_key);
```
### <a name="description"></a><span data-ttu-id="aa55c-559">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-559">Description</span></span>

<span data-ttu-id="aa55c-560">Ta usługa tworzy klucz SHA, który może być używany do uwierzytelniania i szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="aa55c-560">This service creates a SHA key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="aa55c-561">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="aa55c-561">This service is deprecated.</span></span> <span data-ttu-id="aa55c-562">Deweloperzy są zachęcani do migracji do *nx_snmp_agent_sha_key_create_extended ()*.</span><span class="sxs-lookup"><span data-stu-id="aa55c-562">Developers are encouraged to migrate to *nx_snmp_agent_sha_key_create_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-563">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-563">Input Parameters</span></span>

- <span data-ttu-id="aa55c-564">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-564">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-565">**hasło** Wskaźnik na ciąg hasła.</span><span class="sxs-lookup"><span data-stu-id="aa55c-565">**password** Pointer to password string.</span></span>
- <span data-ttu-id="aa55c-566">**destination_key** Wskaźnik do struktury danych klucza SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-566">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-567">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-567">Return Values</span></span>

- <span data-ttu-id="aa55c-568">Pomyślnie utworzono klucz **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="aa55c-568">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="aa55c-569">Błąd tworzenia klucza **NX_SNMP_ERROR** (0x100).</span><span class="sxs-lookup"><span data-stu-id="aa55c-569">**NX_SNMP_ERROR** (0x100) Key create error.</span></span>
- <span data-ttu-id="aa55c-570">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik agenta lub klucza SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-570">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent or key pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-571">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-571">Allowed From</span></span>

<span data-ttu-id="aa55c-572">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-572">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-573">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-573">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_sha_key_create_extended"></a><span data-ttu-id="aa55c-574">nx_snmp_agent_sha_key_create_extended</span><span class="sxs-lookup"><span data-stu-id="aa55c-574">nx_snmp_agent_sha_key_create_extended</span></span>
<span data-ttu-id="aa55c-575">Utwórz klucz SHA (tylko protokół SNMP v3)</span><span class="sxs-lookup"><span data-stu-id="aa55c-575">Create SHA key (SNMP v3 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-576">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-576">Prototype</span></span>

```c
UINT nx_snmp_agent_sha_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY  
                                           *destination_key);
```
### <a name="description"></a><span data-ttu-id="aa55c-577">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-577">Description</span></span>

<span data-ttu-id="aa55c-578">Ta usługa tworzy klucz SHA, który może być używany do uwierzytelniania i szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="aa55c-578">This service creates a SHA key that can be used for authentication and encryption.</span></span>

<span data-ttu-id="aa55c-579">Ta usługa zastępuje *nx_snmp_agent_sha_key_create ().*</span><span class="sxs-lookup"><span data-stu-id="aa55c-579">This service replaces *nx_snmp_agent_sha_key_create().*</span></span> <span data-ttu-id="aa55c-580">Ta wersja wymaga, aby obiekt wywołujący dostarczał długość hasła.</span><span class="sxs-lookup"><span data-stu-id="aa55c-580">This version requires caller to supply password length.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-581">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-581">Input Parameters</span></span>

- <span data-ttu-id="aa55c-582">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-582">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-583">**hasło** Wskaźnik na ciąg hasła.</span><span class="sxs-lookup"><span data-stu-id="aa55c-583">**password** Pointer to password string.</span></span>
- <span data-ttu-id="aa55c-584">**password_length** Długość ciągu hasła.</span><span class="sxs-lookup"><span data-stu-id="aa55c-584">**password_length** Length of password string.</span></span>
- <span data-ttu-id="aa55c-585">**destination_key** Wskaźnik do struktury danych klucza SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-585">**destination_key** Pointer to SNMP key data structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-586">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-586">Return Values</span></span>

- <span data-ttu-id="aa55c-587">Pomyślnie utworzono klucz **NX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="aa55c-587">**NX_SUCCESS** (0x00) Successful key create.</span></span>
- <span data-ttu-id="aa55c-588">Błąd tworzenia klucza **NX_SNMP_ERROR** (0x100).</span><span class="sxs-lookup"><span data-stu-id="aa55c-588">**NX_SNMP_ERROR** (0x100) Key create error.</span></span>
- <span data-ttu-id="aa55c-589">Tworzenie klucza **NX_SNMP_FAILED** (0x102) nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="aa55c-589">**NX_SNMP_FAILED** (0x102) Key create failed.</span></span>
- <span data-ttu-id="aa55c-590">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik agenta lub klucza SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-590">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent or key pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-591">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-591">Allowed From</span></span>

<span data-ttu-id="aa55c-592">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-592">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-593">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-593">Example</span></span>

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_start"></a><span data-ttu-id="aa55c-594">nx_snmp_agent_start</span><span class="sxs-lookup"><span data-stu-id="aa55c-594">nx_snmp_agent_start</span></span>
<span data-ttu-id="aa55c-595">Uruchom agenta SNMP</span><span class="sxs-lookup"><span data-stu-id="aa55c-595">Start SNMP agent</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-596">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-596">Prototype</span></span>

```c
UINT nx_snmp_agent_start(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="aa55c-597">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-597">Description</span></span>

<span data-ttu-id="aa55c-598">Ta usługa wiąże gniazdo UDP z portem SNMP 161 i uruchamia zadanie wątku agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-598">This service binds the UDP socket to the SNMP port 161 and starts the SNMP Agent thread task.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-599">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-599">Input Parameters</span></span>

- <span data-ttu-id="aa55c-600">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-600">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-601">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-601">Return Values</span></span>

- <span data-ttu-id="aa55c-602">**NX_SUCCESS** (0X00) pomyślne uruchomienie agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-602">**NX_SUCCESS** (0x00) Successful start of SNMP Agent.</span></span>
- <span data-ttu-id="aa55c-603">**NX_SNMP_ERROR** (0x100) błąd uruchamiania agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-603">**NX_SNMP_ERROR** (0x100) SNMP Agent start error.</span></span>
- <span data-ttu-id="aa55c-604">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-604">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-605">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-605">Allowed From</span></span>

<span data-ttu-id="aa55c-606">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-606">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-607">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-607">Example</span></span>

```c
/* Start the previously created SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_start(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been started.  */
```
## <a name="nx_snmp_agent_stop"></a><span data-ttu-id="aa55c-608">nx_snmp_agent_stop</span><span class="sxs-lookup"><span data-stu-id="aa55c-608">nx_snmp_agent_stop</span></span>
<span data-ttu-id="aa55c-609">Zatrzymaj agenta SNMP</span><span class="sxs-lookup"><span data-stu-id="aa55c-609">Stop SNMP agent</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-610">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-610">Prototype</span></span>

```c
UINT nx_snmp_agent_stop(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a><span data-ttu-id="aa55c-611">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-611">Description</span></span>

<span data-ttu-id="aa55c-612">Ta usługa przerywa zadanie wątku agenta SNMP i rozwiąże gniazdo UDP z portem SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-612">This service stops the SNMP Agent thread task and unbinds the UDP socket to the SNMP port.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-613">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-613">Input Parameters</span></span>

- <span data-ttu-id="aa55c-614">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-614">**agent_ptr** Pointer to SNMP Agent control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-615">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-615">Return Values</span></span>

- <span data-ttu-id="aa55c-616">**NX_SUCCESS** (0X00) pomyślne zatrzymanie agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-616">**NX_SUCCESS** (0x00) Successful stop of SNMP Agent.</span></span>
- <span data-ttu-id="aa55c-617">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-617">**NX_PTR_ERROR** (0x07) Invalid SNMP Agent pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-618">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-618">Allowed From</span></span>

<span data-ttu-id="aa55c-619">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-619">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-620">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-620">Example</span></span>

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a><span data-ttu-id="aa55c-621">nx_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-621">nx_snmp_agent_trap_send</span></span>
<span data-ttu-id="aa55c-622">Wyślij pułapki SNMPv1 *(tylko IPv4)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-622">Send SNMPv1 trap *(IPv4 only)*</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-623">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-623">Prototype</span></span>

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a><span data-ttu-id="aa55c-624">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-624">Description</span></span>

<span data-ttu-id="aa55c-625">Ta usługa wysyła pułapkę SNMP do menedżera SNMP na określonym adresie IPv4.</span><span class="sxs-lookup"><span data-stu-id="aa55c-625">This service sends an SNMP trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="aa55c-626">Preferowaną metodą wysyłania pułapki SNMP w NetX Duo jest użycie usługi *nxd_snmp_agent_trap_send* .</span><span class="sxs-lookup"><span data-stu-id="aa55c-626">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trap_send* service.</span></span> <span data-ttu-id="aa55c-627">*nx_snmp_agent_trap_send* jest zawarty w NetX Duo do obsługi istniejących aplikacji agenta SNMP NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-627">*nx_snmp_agent_trap_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-628">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-628">Input Parameters</span></span>

- <span data-ttu-id="aa55c-629">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-629">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-630">**IP_address** Adres IPv4 menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-630">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="aa55c-631">**przedsiębiorstwo** Ciąg identyfikatora obiektu przedsiębiorstwa (sysObectID).</span><span class="sxs-lookup"><span data-stu-id="aa55c-631">**enterprise** Enterprise object ID string (sysObectID).</span></span>
- <span data-ttu-id="aa55c-632">**trap_type** Typ żądania pułapki w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="aa55c-632">**trap_type** Type of trap requested, as follows:</span></span>  
   - <span data-ttu-id="aa55c-633">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="aa55c-633">NX_SNMP_TRAP_COLDSTART (0)</span></span>  
   - <span data-ttu-id="aa55c-634">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="aa55c-634">NX_SNMP_TRAP_WARMSTART (1)</span></span>  
   - <span data-ttu-id="aa55c-635">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="aa55c-635">NX_SNMP_TRAP_LINKDOWN (2)</span></span>  
   - <span data-ttu-id="aa55c-636">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="aa55c-636">NX_SNMP_TRAP_LINKUP (3)</span></span>  
   - <span data-ttu-id="aa55c-637">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="aa55c-637">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>  
   - <span data-ttu-id="aa55c-638">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="aa55c-638">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>  

- <span data-ttu-id="aa55c-639">**trap_code** Konkretny kod pułapki.</span><span class="sxs-lookup"><span data-stu-id="aa55c-639">**trap_code** Specific trap code.</span></span>
- <span data-ttu-id="aa55c-640">**elapsed_time** System czasu został osiągnięty (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="aa55c-640">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="aa55c-641">**object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-641">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="aa55c-642">Lista została zakończona NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="aa55c-642">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-643">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-643">Return Values</span></span>

- <span data-ttu-id="aa55c-644">**NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-644">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="aa55c-645">**NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-645">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="aa55c-646">**NX_NOT_ENABLED** (0X14) SNMPv1 nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="aa55c-646">**NX_NOT_ENABLED** (0x14) SNMPv1 not enabled.</span></span>
- <span data-ttu-id="aa55c-647">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-647">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-648">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-648">Allowed From</span></span>

<span data-ttu-id="aa55c-649">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-649">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-650">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-650">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nx_snmp_agent_trap_send(&my_agent,dest_ip_address,
                                   "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, 
                                  tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trap_send"></a><span data-ttu-id="aa55c-651">nxd_snmp_agent_trap_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-651">nxd_snmp_agent_trap_send</span></span>
<span data-ttu-id="aa55c-652">Wyślij pułapki SNMPv1 *(IPv4 i IPv6)*</span><span class="sxs-lookup"><span data-stu-id="aa55c-652">Send SNMPv1 trap *(IPv4 and IPv6)*</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-653">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-653">Prototype</span></span>

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="aa55c-654">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-654">Description</span></span>

<span data-ttu-id="aa55c-655">Ta usługa wysyła pułapkę SNMP do menedżera SNMP na określonym adresie IP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-655">This service sends an SNMP trap to the SNMP Manager at the specified IP address.</span></span> <span data-ttu-id="aa55c-656">Równoważną metodą wysyłania pułapki SNMP w NetX jest usługa *nxd_snmp_agent_trap_send* .</span><span class="sxs-lookup"><span data-stu-id="aa55c-656">The equivalent method for sending an SNMP trap in NetX is the *nxd_snmp_agent_trap_send* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-657">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-657">Input Parameters</span></span>

- <span data-ttu-id="aa55c-658">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-658">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-659">**IP_address** Adres IPv4 lub IPv6 menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-659">**ip_address** IPv4 or IPv6 address of the SNMP Manager.</span></span>
- <span data-ttu-id="aa55c-660">**przedsiębiorstwo** Ciąg identyfikatora obiektu przedsiębiorstwa (sysObectID).</span><span class="sxs-lookup"><span data-stu-id="aa55c-660">**enterprise** Enterprise object ID string (sysObectID).</span></span>
- <span data-ttu-id="aa55c-661">**trap_type** Typ żądania pułapki w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="aa55c-661">**trap_type** Type of trap requested, as follows:</span></span>  
   - <span data-ttu-id="aa55c-662">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="aa55c-662">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="aa55c-663">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="aa55c-663">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="aa55c-664">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="aa55c-664">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="aa55c-665">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="aa55c-665">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="aa55c-666">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="aa55c-666">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="aa55c-667">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="aa55c-667">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

- <span data-ttu-id="aa55c-668">**trap_code** Konkretny kod pułapki.</span><span class="sxs-lookup"><span data-stu-id="aa55c-668">**trap_code** Specific trap code.</span></span>
- <span data-ttu-id="aa55c-669">**elapsed_time** System czasu został osiągnięty (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="aa55c-669">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="aa55c-670">**object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-670">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="aa55c-671">Lista została zakończona NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="aa55c-671">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-672">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-672">Return Values</span></span>

- <span data-ttu-id="aa55c-673">**NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-673">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="aa55c-674">**NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-674">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="aa55c-675">**NX_NOT_ENABLED** (0X14) SNMPv1 nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="aa55c-675">**NX_NOT_ENABLED** (0x14) SNMPv1 not enabled.</span></span>
- <span data-ttu-id="aa55c-676">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-676">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-677">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-677">Allowed From</span></span>

<span data-ttu-id="aa55c-678">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-678">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-679">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-679">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nxd_snmp_agent_trap_send(&my_agent,&dest_ip_address,
                 "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, tx_time_get(), 
               trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_send"></a><span data-ttu-id="aa55c-680">nx_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-680">nx_snmp_agent_trapv2_send</span></span>
<span data-ttu-id="aa55c-681">Wyślij pułapkę SNMPv2 (tylko IPv4)</span><span class="sxs-lookup"><span data-stu-id="aa55c-681">Send SNMPv2 trap (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-682">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-682">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="aa55c-683">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-683">Description</span></span>

<span data-ttu-id="aa55c-684">Ta usługa wysyła pułapkę SNMPv2 do menedżera SNMP na określonym adresie IPv4.</span><span class="sxs-lookup"><span data-stu-id="aa55c-684">This service sends an SNMPv2 trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="aa55c-685">Preferowaną metodą wysyłania pułapki SNMP w NetX Duo jest użycie usługi *nxd_snmp_agent_trapv2_send* .</span><span class="sxs-lookup"><span data-stu-id="aa55c-685">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trapv2_send* service.</span></span> <span data-ttu-id="aa55c-686">*nx_snmp_agent_trapv2_send* jest zawarty w NetX Duo do obsługi istniejących aplikacji agenta SNMP NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-686">*nx_snmp_agent_trapv2_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-687">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-687">Input Parameters</span></span>

- <span data-ttu-id="aa55c-688">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-688">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-689">**IP_address** Adres IPv4 menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-689">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="aa55c-690">**społeczność** Nazwa Wspólnoty (username).</span><span class="sxs-lookup"><span data-stu-id="aa55c-690">**community** Community name (username).</span></span>
- <span data-ttu-id="aa55c-691">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="aa55c-691">**trap_type**</span></span>  
   <span data-ttu-id="aa55c-692">Typ żądanego pułapki.</span><span class="sxs-lookup"><span data-stu-id="aa55c-692">Type of trap requested.</span></span> <span data-ttu-id="aa55c-693">Standardowe zdarzenia to:</span><span class="sxs-lookup"><span data-stu-id="aa55c-693">The standard events are:</span></span>  
   - <span data-ttu-id="aa55c-694">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="aa55c-694">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="aa55c-695">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="aa55c-695">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="aa55c-696">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="aa55c-696">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="aa55c-697">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="aa55c-697">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="aa55c-698">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="aa55c-698">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="aa55c-699">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="aa55c-699">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="aa55c-700">W przypadku danych zastrzeżonych:</span><span class="sxs-lookup"><span data-stu-id="aa55c-700">For proprietary data:</span></span>  
   - <span data-ttu-id="aa55c-701">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (zdefiniowane w *nxd_snmp. h*)</span><span class="sxs-lookup"><span data-stu-id="aa55c-701">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>
   
- <span data-ttu-id="aa55c-702">**elapsed_time** System czasu został osiągnięty (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="aa55c-702">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="aa55c-703">**object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-703">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="aa55c-704">Lista została zakończona NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="aa55c-704">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-705">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-705">Return Values</span></span>

- <span data-ttu-id="aa55c-706">**NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-706">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="aa55c-707">**NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-707">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="aa55c-708">**NX_NOT_ENABLED** (0X14) SNMPv2 nie jest włączony.</span><span class="sxs-lookup"><span data-stu-id="aa55c-708">**NX_NOT_ENABLED** (0x14) SNMPv2 not enabled.</span></span>
- <span data-ttu-id="aa55c-709">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-709">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-710">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-710">Allowed From</span></span>

<span data-ttu-id="aa55c-711">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-711">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-712">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-712">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG  dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_send(&my_agent,dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_oid_send"></a><span data-ttu-id="aa55c-713">nx_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-713">nx_snmp_agent_trapv2_oid_send</span></span>
<span data-ttu-id="aa55c-714">Wysyłanie pułapki SNMPv2 Określanie identyfikatora OID bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="aa55c-714">Send SNMPv2 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-715">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-715">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="aa55c-716">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-716">Description</span></span>

<span data-ttu-id="aa55c-717">Ta usługa wysyła pułapkę SNMPv2 do menedżera SNMP pod określonym adresem IP (tylko IPv4) i umożliwia obiektowi wywołującemu bezpośrednie określenie identyfikatora OID.</span><span class="sxs-lookup"><span data-stu-id="aa55c-717">This service sends an SNMPv2 trap to the SNMP Manager at the specified IP address (IPv4 only) and allows the caller to specify the OID directly.</span></span> <span data-ttu-id="aa55c-718">Preferowaną metodą wysyłania pułapki SNMP z określonym identyfikatorem OID w NetX Duo jest użycie usługi *nxd_snmp_agent_trapv2_oid_send* .</span><span class="sxs-lookup"><span data-stu-id="aa55c-718">The preferred method for sending an SNMP trap with specified OID in NetX Duo is to use the *nxd_snmp_agent_trapv2_oid_send* service.</span></span> <span data-ttu-id="aa55c-719">*nx_snmp_agent_trapv2_oid_ Send* jest zawarty w NetX Duo do obsługi istniejących aplikacji agenta SNMP NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-719">*nx_snmp_agent_trapv2_oid_ send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-720">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-720">Input Parameters</span></span>

- <span data-ttu-id="aa55c-721">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-721">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-722">**IP_address** Adres IP menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-722">**ip_address** IP address of SNMP Manager.</span></span>
- <span data-ttu-id="aa55c-723">**społeczność** Nazwa Wspólnoty (username).</span><span class="sxs-lookup"><span data-stu-id="aa55c-723">**community** Community name (username).</span></span>
- <span data-ttu-id="aa55c-724">**Identyfikator OID** Wskaźnik do buforu zawierającego identyfikator OID.</span><span class="sxs-lookup"><span data-stu-id="aa55c-724">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="aa55c-725">**elapsed_time** System czasu został osiągnięty (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="aa55c-725">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="aa55c-726">**object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-726">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="aa55c-727">Lista została zakończona NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="aa55c-727">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-728">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-728">Return Values</span></span>

- <span data-ttu-id="aa55c-729">**NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-729">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="aa55c-730">**NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-730">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="aa55c-731">**NX_PTR_ERROR** (0X16) Nieprawidłowy wskaźnik agenta lub parametru SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-731">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="aa55c-732">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy docelowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-732">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="aa55c-733">**NX_OPTION_ERROR** (0X0a) nieprawidłowy parametr.</span><span class="sxs-lookup"><span data-stu-id="aa55c-733">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-734">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-734">Allowed From</span></span>

<span data-ttu-id="aa55c-735">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-735">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-736">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-736">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_send"></a><span data-ttu-id="aa55c-737">nxd_snmp_agent_trapv2_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-737">nxd_snmp_agent_trapv2_send</span></span>
<span data-ttu-id="aa55c-738">Wysyłanie pułapki SNMPv2 (IPv4 i IPv6)</span><span class="sxs-lookup"><span data-stu-id="aa55c-738">Send SNMPv2 trap (IPv4 and IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-739">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-739">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *community, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="aa55c-740">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-740">Description</span></span>

<span data-ttu-id="aa55c-741">Ta usługa wysyła do menedżera SNMP pułapkę SNMP v2 o określonym adresie IP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-741">This service sends an SNMP V2 trap to the SNMP Manager at the specified IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-742">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-742">Input Parameters</span></span>

- <span data-ttu-id="aa55c-743">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-743">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-744">**IP_address** Adres IP (IPv4 lub IPv6) menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-744">**ip_address** IP (IPv4 or IPv6) address of the SNMP Manager.</span></span>
- <span data-ttu-id="aa55c-745">**społeczność** Nazwa Wspólnoty (username).</span><span class="sxs-lookup"><span data-stu-id="aa55c-745">**community** Community name (username).</span></span>
- <span data-ttu-id="aa55c-746">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="aa55c-746">**trap_type**</span></span>  
   <span data-ttu-id="aa55c-747">Typ żądanego pułapki.</span><span class="sxs-lookup"><span data-stu-id="aa55c-747">Type of trap requested.</span></span> <span data-ttu-id="aa55c-748">Standardowe zdarzenia to:</span><span class="sxs-lookup"><span data-stu-id="aa55c-748">The standard events are:</span></span>  
   - <span data-ttu-id="aa55c-749">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="aa55c-749">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="aa55c-750">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="aa55c-750">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="aa55c-751">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="aa55c-751">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="aa55c-752">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="aa55c-752">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="aa55c-753">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="aa55c-753">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="aa55c-754">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="aa55c-754">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="aa55c-755">W przypadku danych zastrzeżonych:</span><span class="sxs-lookup"><span data-stu-id="aa55c-755">For proprietary data:</span></span>

   - <span data-ttu-id="aa55c-756">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (zdefiniowane w *nxd_snmp. h*)</span><span class="sxs-lookup"><span data-stu-id="aa55c-756">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="aa55c-757">**elapsed_time** System czasu został osiągnięty (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="aa55c-757">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="aa55c-758">**object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-758">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="aa55c-759">Lista została zakończona NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="aa55c-759">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-760">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-760">Return Values</span></span>

- <span data-ttu-id="aa55c-761">**NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-761">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="aa55c-762">**NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-762">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="aa55c-763">**NX_NOT_ENABLED** (0X14) SNMPv2 nie jest włączony.</span><span class="sxs-lookup"><span data-stu-id="aa55c-763">**NX_NOT_ENABLED** (0x14) SNMPv2 not enabled.</span></span>
- <span data-ttu-id="aa55c-764">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) nieobsługiwana wersja protokołu IP</span><span class="sxs-lookup"><span data-stu-id="aa55c-764">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Unsupported IP version</span></span>
- <span data-ttu-id="aa55c-765">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-765">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-766">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-766">Allowed From</span></span>

<span data-ttu-id="aa55c-767">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-767">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-768">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-768">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send a standard event trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_send(&my_agent,&dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_oid_send"></a><span data-ttu-id="aa55c-769">nxd_snmp_agent_trapv2_oid_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-769">nxd_snmp_agent_trapv2_oid_send</span></span>
<span data-ttu-id="aa55c-770">Wysyłanie pułapki SNMPv2 Określanie identyfikatora OID bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="aa55c-770">Send SNMPv2 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-771">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-771">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *community,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                    *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="aa55c-772">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-772">Description</span></span>

<span data-ttu-id="aa55c-773">Ta usługa wysyła pułapkę protokołu SNMP v2 do menedżera SNMP pod określonym adresem IP (IPv4/IPv6) i umożliwia obiektowi wywołującemu bezpośrednie określenie identyfikatora OID.</span><span class="sxs-lookup"><span data-stu-id="aa55c-773">This service sends an SNMP v2 trap to the SNMP Manager at the specified IP address (IPv4/IPv6) and allows the caller to specify the OID directly.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-774">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-774">Input Parameters</span></span>

- <span data-ttu-id="aa55c-775">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-775">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-776">**IP_address** Adres IP menedżera SNMP (IPv4/IPv6).</span><span class="sxs-lookup"><span data-stu-id="aa55c-776">**ip_address** IP address of SNMP Manager (IPv4/IPv6).</span></span>
- <span data-ttu-id="aa55c-777">**społeczność** Nazwa Wspólnoty (username).</span><span class="sxs-lookup"><span data-stu-id="aa55c-777">**community** Community name (username).</span></span>
- <span data-ttu-id="aa55c-778">**Identyfikator OID** Wskaźnik do buforu zawierającego identyfikator OID.</span><span class="sxs-lookup"><span data-stu-id="aa55c-778">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="aa55c-779">**elapsed_time** System czasu został osiągnięty (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="aa55c-779">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="aa55c-780">**object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-780">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="aa55c-781">Lista została zakończona NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="aa55c-781">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-782">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-782">Return Values</span></span>

- <span data-ttu-id="aa55c-783">**NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-783">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="aa55c-784">**NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-784">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="aa55c-785">**NX_PTR_ERROR** (0X16) Nieprawidłowy wskaźnik agenta lub parametru SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-785">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="aa55c-786">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy docelowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-786">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="aa55c-787">**NX_OPTION_ERROR** (0X0a) nieprawidłowy parametr.</span><span class="sxs-lookup"><span data-stu-id="aa55c-787">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-788">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-788">Allowed From</span></span>

<span data-ttu-id="aa55c-789">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-789">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-790">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-790">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS         address;


/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

address.nxd_ip_version = NX_IP_VERSION_V4;
address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61)

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_oid_send(&my_agent, &address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_trapv3_send"></a><span data-ttu-id="aa55c-791">nx_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-791">nx_snmp_agent_trapv3_send</span></span>
<span data-ttu-id="aa55c-792">Wyślij pułapkę SNMPv3 (tylko IPv4)</span><span class="sxs-lookup"><span data-stu-id="aa55c-792">Send SNMPv3 trap (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-793">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-793">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a><span data-ttu-id="aa55c-794">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-794">Description</span></span>

<span data-ttu-id="aa55c-795">Ta usługa wysyła pułapki SNMPv3 do menedżera SNMP na określonym adresie IPv4.</span><span class="sxs-lookup"><span data-stu-id="aa55c-795">This service sends an SNMPv3 trap to the SNMP Manager at the specified IPv4 address.</span></span> <span data-ttu-id="aa55c-796">Preferowaną metodą wysyłania pułapki SNMP w NetX Duo jest użycie usługi *nxd_snmp_agent_trapv3_send* .</span><span class="sxs-lookup"><span data-stu-id="aa55c-796">The preferred method for sending an SNMP trap in NetX Duo is to use the *nxd_snmp_agent_trapv3_send* service.</span></span> <span data-ttu-id="aa55c-797">*nx_snmp_agent_trapv3_send* jest zawarty w NetX Duo do obsługi istniejących aplikacji agenta SNMP NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-797">*nx_snmp_agent_trapv3_send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-798">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-798">Input Parameters</span></span>

- <span data-ttu-id="aa55c-799">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-799">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-800">**IP_address** Adres IPv4 menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-800">**ip_address** IPv4 address of the SNMP Manager.</span></span>
- <span data-ttu-id="aa55c-801">**Nazwa użytkownika** Nazwa Wspólnoty (username).</span><span class="sxs-lookup"><span data-stu-id="aa55c-801">**username** Community name (username).</span></span>
- <span data-ttu-id="aa55c-802">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="aa55c-802">**trap_type**</span></span>  
   <span data-ttu-id="aa55c-803">Typ żądanego pułapki.</span><span class="sxs-lookup"><span data-stu-id="aa55c-803">Type of trap requested.</span></span> <span data-ttu-id="aa55c-804">Standardowe zdarzenia to:</span><span class="sxs-lookup"><span data-stu-id="aa55c-804">The standard events are:</span></span>  
   - <span data-ttu-id="aa55c-805">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="aa55c-805">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="aa55c-806">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="aa55c-806">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="aa55c-807">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="aa55c-807">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="aa55c-808">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="aa55c-808">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="aa55c-809">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="aa55c-809">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="aa55c-810">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="aa55c-810">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>

   <span data-ttu-id="aa55c-811">W przypadku danych zastrzeżonych:</span><span class="sxs-lookup"><span data-stu-id="aa55c-811">For proprietary data:</span></span>
   - <span data-ttu-id="aa55c-812">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (zdefiniowane w *nxd_snmp. h*)</span><span class="sxs-lookup"><span data-stu-id="aa55c-812">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="aa55c-813">**elapsed_time** System czasu został osiągnięty (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="aa55c-813">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="aa55c-814">**object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-814">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="aa55c-815">Lista została zakończona NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="aa55c-815">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-816">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-816">Return Values</span></span>

- <span data-ttu-id="aa55c-817">**NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-817">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="aa55c-818">**NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-818">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="aa55c-819">**NX_NOT_ENABLED** (0X14) SNMPv3 nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="aa55c-819">**NX_NOT_ENABLED** (0x14) SNMPv3 not enabled.</span></span>
- <span data-ttu-id="aa55c-820">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-820">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-821">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-821">Allowed From</span></span>

<span data-ttu-id="aa55c-822">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-822">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-823">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-823">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_send(&my_agent, dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv3_oid_send"></a><span data-ttu-id="aa55c-824">nx_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-824">nx_snmp_agent_trapv3_oid_send</span></span>
<span data-ttu-id="aa55c-825">Wysyłanie pułapki SNMPv3 Określanie identyfikatora OID bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="aa55c-825">Send SNMPv3 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-826">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-826">Prototype</span></span>

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="aa55c-827">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-827">Description</span></span>

<span data-ttu-id="aa55c-828">Ta usługa wysyła pułapki SNMPv3 do menedżera SNMP pod określonym adresem IP (tylko IPv4) i umożliwia obiektowi wywołującemu bezpośrednie określenie identyfikatora OID.</span><span class="sxs-lookup"><span data-stu-id="aa55c-828">This service sends an SNMPv3 trap to the SNMP Manager at the specified IP address (IPv4 only) and allows the caller to specify the OID directly.</span></span> <span data-ttu-id="aa55c-829">Preferowaną metodą wysyłania pułapki SNMP z określonym identyfikatorem OID w NetX Duo jest użycie usługi *nxd_snmp_agent_trapv3_oid_send* .</span><span class="sxs-lookup"><span data-stu-id="aa55c-829">The preferred method for sending an SNMP trap with specified OID in NetX Duo is to use the *nxd_snmp_agent_trapv3_oid_send* service.</span></span> <span data-ttu-id="aa55c-830">*nx_snmp_agent_trapv3_oid_ Send* jest zawarty w NetX Duo do obsługi istniejących aplikacji agenta SNMP NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-830">*nx_snmp_agent_trapv3_oid_ send* is included in NetX Duo to support existing NetX SNMP Agent applications.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-831">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-831">Input Parameters</span></span>

- <span data-ttu-id="aa55c-832">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-832">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-833">**IP_address** Adres IP menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-833">**ip_address** IP address of SNMP Manager.</span></span>
- <span data-ttu-id="aa55c-834">**Nazwa użytkownika** Nazwa Wspólnoty (username).</span><span class="sxs-lookup"><span data-stu-id="aa55c-834">**username** Community name (username).</span></span>
- <span data-ttu-id="aa55c-835">**Identyfikator OID** Wskaźnik do buforu zawierającego identyfikator OID.</span><span class="sxs-lookup"><span data-stu-id="aa55c-835">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="aa55c-836">**elapsed_time** System czasu został osiągnięty (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="aa55c-836">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="aa55c-837">**object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-837">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="aa55c-838">Lista została zakończona NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="aa55c-838">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-839">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-839">Return Values</span></span>

- <span data-ttu-id="aa55c-840">**NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-840">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="aa55c-841">**NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-841">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="aa55c-842">**NX_PTR_ERROR** (0X16) Nieprawidłowy wskaźnik agenta lub parametru SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-842">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="aa55c-843">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy docelowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-843">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>
- <span data-ttu-id="aa55c-844">**NX_OPTION_ERROR** (0X0a) nieprawidłowy parametr.</span><span class="sxs-lookup"><span data-stu-id="aa55c-844">**NX_OPTION_ERROR** (0x0a) Invalid parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-845">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-845">Allowed From</span></span>

<span data-ttu-id="aa55c-846">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-846">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-847">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-847">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trapv3_send"></a><span data-ttu-id="aa55c-848">nxd_snmp_agent_trapv3_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-848">nxd_snmp_agent_trapv3_send</span></span>
<span data-ttu-id="aa55c-849">Wysyłanie pułapki SNMPv3 (IPv4 i IPv6)</span><span class="sxs-lookup"><span data-stu-id="aa55c-849">Send SNMPv3 trap (IPv4 and IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-850">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-850">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *username, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="aa55c-851">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-851">Description</span></span>

<span data-ttu-id="aa55c-852">Ta usługa wysyła pułapkę SNMP do menedżera SNMP na określonym adresie IP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-852">This service sends an SNMP trap to the SNMP Manager at the specified IP address.</span></span> <span data-ttu-id="aa55c-853">Ta Pułapka jest zasadniczo taka sama jak pułapka SNMP v2, z wyjątkiem tego, że format komunikatu pułapki jest zawarty w jednostce PDU protokołu SNMP v3.</span><span class="sxs-lookup"><span data-stu-id="aa55c-853">This trap is basically the same as the SNMP v2 trap, except the trap message format is contained in the SNMP v3 PDU.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-854">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-854">Input Parameters</span></span>

- <span data-ttu-id="aa55c-855">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-855">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-856">**IP_address** Adres IP (IPv4 lub IPv6) menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-856">**ip_address** IP (IPv4 or IPv6) address of the SNMP Manager.</span></span>
- <span data-ttu-id="aa55c-857">**Nazwa użytkownika** Nazwa Wspólnoty (username).</span><span class="sxs-lookup"><span data-stu-id="aa55c-857">**username** Community name (username).</span></span>
- <span data-ttu-id="aa55c-858">**trap_type**</span><span class="sxs-lookup"><span data-stu-id="aa55c-858">**trap_type**</span></span>  
   <span data-ttu-id="aa55c-859">Typ żądanego pułapki.</span><span class="sxs-lookup"><span data-stu-id="aa55c-859">Type of trap requested.</span></span> <span data-ttu-id="aa55c-860">Standardowe zdarzenia to:</span><span class="sxs-lookup"><span data-stu-id="aa55c-860">The standard events are:</span></span>
   - <span data-ttu-id="aa55c-861">NX_SNMP_TRAP_COLDSTART (0)</span><span class="sxs-lookup"><span data-stu-id="aa55c-861">NX_SNMP_TRAP_COLDSTART (0)</span></span>
   - <span data-ttu-id="aa55c-862">NX_SNMP_TRAP_WARMSTART (1)</span><span class="sxs-lookup"><span data-stu-id="aa55c-862">NX_SNMP_TRAP_WARMSTART (1)</span></span>
   - <span data-ttu-id="aa55c-863">NX_SNMP_TRAP_LINKDOWN (2)</span><span class="sxs-lookup"><span data-stu-id="aa55c-863">NX_SNMP_TRAP_LINKDOWN (2)</span></span>
   - <span data-ttu-id="aa55c-864">NX_SNMP_TRAP_LINKUP (3)</span><span class="sxs-lookup"><span data-stu-id="aa55c-864">NX_SNMP_TRAP_LINKUP (3)</span></span>
   - <span data-ttu-id="aa55c-865">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span><span class="sxs-lookup"><span data-stu-id="aa55c-865">NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)</span></span>
   - <span data-ttu-id="aa55c-866">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span><span class="sxs-lookup"><span data-stu-id="aa55c-866">NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)</span></span>  
   <span data-ttu-id="aa55c-867">W przypadku danych zastrzeżonych:</span><span class="sxs-lookup"><span data-stu-id="aa55c-867">For proprietary data:</span></span>
   - <span data-ttu-id="aa55c-868">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (zdefiniowane w *nxd_snmp. h*)</span><span class="sxs-lookup"><span data-stu-id="aa55c-868">NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (defined in *nxd_snmp.h*)</span></span>

- <span data-ttu-id="aa55c-869">**elapsed_time** System czasu został osiągnięty (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="aa55c-869">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="aa55c-870">**object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-870">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="aa55c-871">Lista została zakończona NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="aa55c-871">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-872">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-872">Return Values</span></span>

- <span data-ttu-id="aa55c-873">**NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-873">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="aa55c-874">**NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-874">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="aa55c-875">**NX_NOT_ENABLED** (0X14) SNMPv3 nie jest włączona.</span><span class="sxs-lookup"><span data-stu-id="aa55c-875">**NX_NOT_ENABLED** (0x14) SNMPv3 not enabled.</span></span>
- <span data-ttu-id="aa55c-876">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) nieobsługiwana wersja protokołu IP</span><span class="sxs-lookup"><span data-stu-id="aa55c-876">**NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) Unsupported IP version</span></span>
- <span data-ttu-id="aa55c-877">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-877">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-878">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-878">Allowed From</span></span>

<span data-ttu-id="aa55c-879">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-879">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-880">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-880">Example</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_send(&my_agent, &dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv3_oid_send"></a><span data-ttu-id="aa55c-881">nxd_snmp_agent_trapv3_oid_send</span><span class="sxs-lookup"><span data-stu-id="aa55c-881">nxd_snmp_agent_trapv3_oid_send</span></span>
<span data-ttu-id="aa55c-882">Wysyłanie pułapki SNMPv3 Określanie identyfikatora OID bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="aa55c-882">Send SNMPv3 trap specifying OID directly</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-883">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-883">Prototype</span></span>

```c
UINT nxd_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *username,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a><span data-ttu-id="aa55c-884">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-884">Description</span></span>

<span data-ttu-id="aa55c-885">Ta usługa wysyła pułapki SNMPv3 do menedżera SNMP przy użyciu określonego adresu IP (IPv4/IPv6) i umożliwia obiektowi wywołującemu bezpośrednie określenie identyfikatora OID.</span><span class="sxs-lookup"><span data-stu-id="aa55c-885">This service sends an SNMPv3 trap to the SNMP Manager at the specified IP address (IPv4/IPv6) and allows the caller to specify the OID directly.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-886">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-886">Input Parameters</span></span>

- <span data-ttu-id="aa55c-887">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-887">**agent_ptr** Pointer to SNMP Agent control block.</span></span>
- <span data-ttu-id="aa55c-888">**IP_address** Wskaźnik na adres IP menedżera SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-888">**ip_address** Pointer to IP address of SNMP Manager.</span></span>
- <span data-ttu-id="aa55c-889">**Nazwa użytkownika** Nazwa użytkownika (nazwa Wspólnoty).</span><span class="sxs-lookup"><span data-stu-id="aa55c-889">**username** Username (community name).</span></span>
- <span data-ttu-id="aa55c-890">**Identyfikator OID** Wskaźnik do buforu zawierającego identyfikator OID.</span><span class="sxs-lookup"><span data-stu-id="aa55c-890">**oid** Pointer to buffer containing OID.</span></span>
- <span data-ttu-id="aa55c-891">**elapsed_time** System czasu został osiągnięty (sysUpTime).</span><span class="sxs-lookup"><span data-stu-id="aa55c-891">**elapsed_time** Time system has been up (sysUpTime).</span></span>
- <span data-ttu-id="aa55c-892">**object_list_ptr** Tablica obiektów i ich skojarzone wartości do uwzględnienia w pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-892">**object_list_ptr** Array of objects and their associated values to be included in the SNMP trap.</span></span> <span data-ttu-id="aa55c-893">Lista została zakończona NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="aa55c-893">The list is NX_NULL terminated.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-894">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-894">Return Values</span></span>

- <span data-ttu-id="aa55c-895">**NX_SUCCESS** (0X00) pomyślne wysłanie pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-895">**NX_SUCCESS** (0x00) Successful SNMP trap send.</span></span>
- <span data-ttu-id="aa55c-896">**NX_SNMP_ERROR** (0X100) błąd podczas wysyłania pułapki SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-896">**NX_SNMP_ERROR** (0x100) Error sending SNMP trap.</span></span>
- <span data-ttu-id="aa55c-897">**NX_PTR_ERROR** (0X16) Nieprawidłowy wskaźnik agenta lub parametru SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-897">**NX_PTR_ERROR** (0x16) Invalid SNMP Agent or parameter pointer.</span></span>
- <span data-ttu-id="aa55c-898">**NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy docelowy adres IP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-898">**NX_IP_ADDRESS_ERROR** (0x21) Invalid destination IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-899">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-899">Allowed From</span></span>

<span data-ttu-id="aa55c-900">Wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-900">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-901">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-901">Example</span></span>

```c
NXD_ADDRESS         ip_address;
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

ip_address.nxd_ip_version = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61);

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_oid_send(&my_agent, &ip_address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_v3_context_boots_set"></a><span data-ttu-id="aa55c-902">nx_snmp_agent_v3_context_boots_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-902">nx_snmp_agent_v3_context_boots_set</span></span>
<span data-ttu-id="aa55c-903">Ustaw liczbę ponownych uruchomień (Jeśli włączono funkcję SNMPv3)</span><span class="sxs-lookup"><span data-stu-id="aa55c-903">Set the number of reboots (if SNMPv3 enabled)</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-904">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-904">Prototype</span></span>

```c
UINT nx_snmp_agent_v3_context_boots_set(NX_SNMP_AGENT *agent_ptr, 
                                        UINT boots);
```

### <a name="description"></a><span data-ttu-id="aa55c-905">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-905">Description</span></span>

<span data-ttu-id="aa55c-906">Ta usługa ustawia liczbę ponownych uruchomień zarejestrowanych przez agenta SNMP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-906">This service sets the number of reboots recorded by the SNMP agent.</span></span> <span data-ttu-id="aa55c-907">Ta usługa jest dostępna tylko wtedy, gdy dla agenta SNMP jest włączona funkcja SNMPv3, ponieważ liczba rozruchowych jest używana tylko w protokole SNMPv3.</span><span class="sxs-lookup"><span data-stu-id="aa55c-907">This service is only available if SNMPv3 is enabled for the SNMP agent because boot count is only used in the SNMPv3 protocol.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-908">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-908">Input Parameters</span></span>

- <span data-ttu-id="aa55c-909">**agent_ptr** Wskaźnik do bloku sterowania agentami SNMP</span><span class="sxs-lookup"><span data-stu-id="aa55c-909">**agent_ptr** Pointer to SNMP Agent control block</span></span>
- <span data-ttu-id="aa55c-910">**rozruch** Wartość, dla której ma zostać ustawiona liczba rozruchowych agentów SNMP</span><span class="sxs-lookup"><span data-stu-id="aa55c-910">**boots** The value to set SNMP Agent boot count to</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-911">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-911">Return Values</span></span>

- <span data-ttu-id="aa55c-912">**NX_SUCCESS** (0X00) pomyślnie ustawił liczbę rozruchów</span><span class="sxs-lookup"><span data-stu-id="aa55c-912">**NX_SUCCESS** (0x00) Successfully set boot count</span></span>
- <span data-ttu-id="aa55c-913">**NX_SNMP_ERROR** (0x100) — Ustawianie błędu liczby rozruchowych</span><span class="sxs-lookup"><span data-stu-id="aa55c-913">**NX_SNMP_ERROR** (0x100) Error setting boot count</span></span>
- <span data-ttu-id="aa55c-914">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-914">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-915">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-915">Allowed From</span></span>

<span data-ttu-id="aa55c-916">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-916">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-917">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-917">Example</span></span>

```c
UINT my_boots = 4;

if (my_agent.nx_snmp_agent_v3_enabled == NX_TRUE)
{
   status = nx_snmp_agent_v3_context_boots_set(&my_agent, my_boots);
}


/* If status is NX_SUCCESS the SNMP boot count is set.  */
```

## <a name="nx_snmp_object_compare"></a><span data-ttu-id="aa55c-918">nx_snmp_object_compare</span><span class="sxs-lookup"><span data-stu-id="aa55c-918">nx_snmp_object_compare</span></span>
<span data-ttu-id="aa55c-919">Porównaj dwa obiekty</span><span class="sxs-lookup"><span data-stu-id="aa55c-919">Compare two objects</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-920">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-920">Prototype</span></span>

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a><span data-ttu-id="aa55c-921">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-921">Description</span></span>

<span data-ttu-id="aa55c-922">Ta usługa porównuje podany identyfikator obiektu z IDENTYFIKATORem obiektu odwołania.</span><span class="sxs-lookup"><span data-stu-id="aa55c-922">This service compares the supplied object ID with the reference object ID.</span></span> <span data-ttu-id="aa55c-923">Oba identyfikatory obiektów znajdują się w notacji typu ASCII SMI, np. oba obiekty muszą zaczynać się od ciągu ASCII "1.3.6".</span><span class="sxs-lookup"><span data-stu-id="aa55c-923">Both object IDs are in the ASCII SMI notation, e.g., both object must start with the ASCII string “1.3.6”.</span></span>

<span data-ttu-id="aa55c-924">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="aa55c-924">This service is deprecated.</span></span> <span data-ttu-id="aa55c-925">Deweloperzy są zachęcani do migracji do *nx_snmp_object_compare_extended ().*</span><span class="sxs-lookup"><span data-stu-id="aa55c-925">Developers are encouraged to migrate to *nx_snmp_object_compare_extended().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-926">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-926">Input Parameters</span></span>

- <span data-ttu-id="aa55c-927">**obiekt** Wskaźnik do obiektu ID.</span><span class="sxs-lookup"><span data-stu-id="aa55c-927">**object** Pointer to object ID.</span></span>
- <span data-ttu-id="aa55c-928">**reference_object** Wskaźnik na identyfikator obiektu odwołania.</span><span class="sxs-lookup"><span data-stu-id="aa55c-928">**reference_object** Pointer to the reference object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-929">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-929">Return Values</span></span>

- <span data-ttu-id="aa55c-930">**NX_SUCCESS** (0x00) obiekt jest zgodny z obiektem Reference.</span><span class="sxs-lookup"><span data-stu-id="aa55c-930">**NX_SUCCESS** (0x00) The object matches the reference object.</span></span>
- <span data-ttu-id="aa55c-931">**NX_SNMP_NEXT_ENTRY** (0x101) obiekt jest mniejszy niż obiekt Reference.</span><span class="sxs-lookup"><span data-stu-id="aa55c-931">**NX_SNMP_NEXT_ENTRY** (0x101) The object is less than the reference object.</span></span>
- <span data-ttu-id="aa55c-932">**NX_SNMP_ERROR** (0x100) obiekt jest większy niż obiekt Reference.</span><span class="sxs-lookup"><span data-stu-id="aa55c-932">**NX_SNMP_ERROR** (0x100) The object is greater than the reference object.</span></span>
- <span data-ttu-id="aa55c-933">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-933">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-934">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-934">Allowed From</span></span>

<span data-ttu-id="aa55c-935">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-935">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-936">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-936">Example</span></span>

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare(requested_object, "1.3.6.1.2.1.1.1.0");

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_compare_extended"></a><span data-ttu-id="aa55c-937">nx_snmp_object_compare_extended</span><span class="sxs-lookup"><span data-stu-id="aa55c-937">nx_snmp_object_compare_extended</span></span>
<span data-ttu-id="aa55c-938">Porównaj dwa obiekty</span><span class="sxs-lookup"><span data-stu-id="aa55c-938">Compare two objects</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-939">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-939">Prototype</span></span>

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a><span data-ttu-id="aa55c-940">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-940">Description</span></span>

<span data-ttu-id="aa55c-941">Ta usługa porównuje podany identyfikator obiektu z IDENTYFIKATORem obiektu odwołania.</span><span class="sxs-lookup"><span data-stu-id="aa55c-941">This service compares the supplied object ID with the reference object ID.</span></span> <span data-ttu-id="aa55c-942">Oba identyfikatory obiektów znajdują się w notacji typu ASCII SMI, np. oba obiekty muszą zaczynać się od ciągu ASCII "1.3.6".</span><span class="sxs-lookup"><span data-stu-id="aa55c-942">Both object IDs are in the ASCII SMI notation, e.g., both object must start with the ASCII string “1.3.6”.</span></span>

<span data-ttu-id="aa55c-943">Ta usługa zastępuje *nx_snmp_object_compare ().*</span><span class="sxs-lookup"><span data-stu-id="aa55c-943">This service replaces *nx_snmp_object_compare().*</span></span> <span data-ttu-id="aa55c-944">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości.</span><span class="sxs-lookup"><span data-stu-id="aa55c-944">This version requires callers to supply length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-945">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-945">Input Parameters</span></span>

- <span data-ttu-id="aa55c-946">**request_object** Wskaźnik do żądania identyfikatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-946">**request_object** Pointer to request object ID.</span></span>
- <span data-ttu-id="aa55c-947">**request_object_length** Długość identyfikatora obiektu żądania.</span><span class="sxs-lookup"><span data-stu-id="aa55c-947">**request_object_length** Length of the request object ID.</span></span>
- <span data-ttu-id="aa55c-948">**reference_object** Wskaźnik na identyfikator obiektu odwołania.</span><span class="sxs-lookup"><span data-stu-id="aa55c-948">**reference_object** Pointer to the reference object ID.</span></span>
- <span data-ttu-id="aa55c-949">**reference_object_length** Długość identyfikatora obiektu odwołania.</span><span class="sxs-lookup"><span data-stu-id="aa55c-949">**reference_object_length** Length of the reference object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-950">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-950">Return Values</span></span>

- <span data-ttu-id="aa55c-951">**NX_SUCCESS** (0x00) obiekt jest zgodny z obiektem Reference.</span><span class="sxs-lookup"><span data-stu-id="aa55c-951">**NX_SUCCESS** (0x00) The object matches the reference object.</span></span>
- <span data-ttu-id="aa55c-952">**NX_SNMP_NEXT_ENTRY** (0x101) obiekt jest mniejszy niż obiekt Reference.</span><span class="sxs-lookup"><span data-stu-id="aa55c-952">**NX_SNMP_NEXT_ENTRY** (0x101) The object is less than the reference object.</span></span>
- <span data-ttu-id="aa55c-953">**NX_SNMP_ERROR** (0x100) obiekt jest większy niż obiekt Reference.</span><span class="sxs-lookup"><span data-stu-id="aa55c-953">**NX_SNMP_ERROR** (0x100) The object is greater than the reference object.</span></span>
- <span data-ttu-id="aa55c-954">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-954">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-955">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-955">Allowed From</span></span>

<span data-ttu-id="aa55c-956">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-956">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-957">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-957">Example</span></span>

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare_extended(requested_object, 17,
                                          "1.3.6.1.2.1.1.1.0", 17);

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_copy"></a><span data-ttu-id="aa55c-958">nx_snmp_object_copy</span><span class="sxs-lookup"><span data-stu-id="aa55c-958">nx_snmp_object_copy</span></span>
<span data-ttu-id="aa55c-959">Kopiowanie obiektu</span><span class="sxs-lookup"><span data-stu-id="aa55c-959">Copy an object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-960">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-960">Prototype</span></span>

```c
UINT  nx_snmp_object_copy(UCHAR *source_object_name, 
                          UCHAR *destination_object_name);
```
### <a name="description"></a><span data-ttu-id="aa55c-961">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-961">Description</span></span>

<span data-ttu-id="aa55c-962">Ta usługa kopiuje obiekt źródłowy w notacji programu ASCII SIM do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-962">This service copies the source object in ASCII SIM notation to the destination object.</span></span>

<span data-ttu-id="aa55c-963">Ta usługa jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="aa55c-963">This service is deprecated.</span></span> <span data-ttu-id="aa55c-964">Deweloperzy są zachęcani do migracji do *nx_snmp_object_copy_extended ().*</span><span class="sxs-lookup"><span data-stu-id="aa55c-964">Developers are encouraged to migrate to *nx_snmp_object_copy_extended().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-965">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-965">Input Parameters</span></span>

- <span data-ttu-id="aa55c-966">**source_object_name** Wskaźnik na identyfikator obiektu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-966">**source_object_name** Pointer to source object ID.</span></span>
- <span data-ttu-id="aa55c-967">**destination_object_name** Wskaźnik do docelowego identyfikatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-967">**destination_object_name** Pointer to destination object ID.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-968">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-968">Return Values</span></span>

- <span data-ttu-id="aa55c-969">**rozmiar** Liczba bajtów skopiowanych do nazwy docelowej.</span><span class="sxs-lookup"><span data-stu-id="aa55c-969">**size** Number of bytes copied to destination name.</span></span> <span data-ttu-id="aa55c-970">Jeśli błąd, zwracana jest wartość zero.</span><span class="sxs-lookup"><span data-stu-id="aa55c-970">If error, zero is returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-971">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-971">Allowed From</span></span>

<span data-ttu-id="aa55c-972">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-972">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-973">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-973">Example</span></span>

```c
/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, my_new_object);

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_copy_extended"></a><span data-ttu-id="aa55c-974">nx_snmp_object_copy_extended</span><span class="sxs-lookup"><span data-stu-id="aa55c-974">nx_snmp_object_copy_extended</span></span>
<span data-ttu-id="aa55c-975">Kopiowanie obiektu</span><span class="sxs-lookup"><span data-stu-id="aa55c-975">Copy an object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-976">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-976">Prototype</span></span>

```c
UINT  nx_snmp_object_copy_extended(UCHAR *source_object_name, 
                             UINT source_object_name_length,
                             UCHAR *destination_object_name_buffer,
                             UINT destination_object_name_buffer_size);
```

### <a name="description"></a><span data-ttu-id="aa55c-977">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-977">Description</span></span>

<span data-ttu-id="aa55c-978">Ta usługa kopiuje obiekt źródłowy w notacji programu ASCII SIM do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-978">This service copies the source object in ASCII SIM notation to the destination object.</span></span>

<span data-ttu-id="aa55c-979">Ta usługa zastępuje *nx_snmp_object_copy ().*</span><span class="sxs-lookup"><span data-stu-id="aa55c-979">This service replaces *nx_snmp_object_copy().*</span></span> <span data-ttu-id="aa55c-980">Ta wersja wymaga, aby wywołujący dostarczali informacje o długości.</span><span class="sxs-lookup"><span data-stu-id="aa55c-980">This version requires callers to supply length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-981">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-981">Input Parameters</span></span>

- <span data-ttu-id="aa55c-982">**source_object_name** Wskaźnik na identyfikator obiektu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-982">**source_object_name** Pointer to source object ID.</span></span>
- <span data-ttu-id="aa55c-983">**source_object_name_length** Długość identyfikatora obiektu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-983">**source_object_name_length** Length of source object ID.</span></span>
- <span data-ttu-id="aa55c-984">**destination_object_name_buffer** Wskaźnik do buforu obiektów docelowych.</span><span class="sxs-lookup"><span data-stu-id="aa55c-984">**destination_object_name_buffer** Pointer to destination object buffer.</span></span>
- <span data-ttu-id="aa55c-985">**destination_object_name_buffer_size** Rozmiar buforu obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-985">**destination_object_name_buffer_size** Size of destination object buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-986">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-986">Return Values</span></span>

- <span data-ttu-id="aa55c-987">**rozmiar** Liczba bajtów skopiowanych do nazwy docelowej.</span><span class="sxs-lookup"><span data-stu-id="aa55c-987">**size** Number of bytes copied to destination name.</span></span> <span data-ttu-id="aa55c-988">Jeśli błąd, zwracana jest wartość zero.</span><span class="sxs-lookup"><span data-stu-id="aa55c-988">If error, zero is returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-989">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-989">Allowed From</span></span>

<span data-ttu-id="aa55c-990">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-990">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-991">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-991">Example</span></span>

```c
UCHAR   my_object = "1.3.6.1.2.1.1.1.0";
UCHAR   my_new_object[32];


/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, 17, my_new_object, sizeof(my_new_object));

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_counter_get"></a><span data-ttu-id="aa55c-992">nx_snmp_object_counter_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-992">nx_snmp_object_counter_get</span></span>
<span data-ttu-id="aa55c-993">Pobierz obiekt licznika</span><span class="sxs-lookup"><span data-stu-id="aa55c-993">Get counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-994">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-994">Prototype</span></span>

```c
UINT  nx_snmp_object_counter_get(VOID *source_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a><span data-ttu-id="aa55c-995">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-995">Description</span></span>

<span data-ttu-id="aa55c-996">Ta usługa pobiera obiekt licznika pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-996">This service retrieves the counter object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-997">Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-997">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-998">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-998">Input Parameters</span></span>

- <span data-ttu-id="aa55c-999">**source_ptr** Wskaźnik do źródła licznika.</span><span class="sxs-lookup"><span data-stu-id="aa55c-999">**source_ptr** Pointer to counter source.</span></span>
- <span data-ttu-id="aa55c-1000">**object_data** Wskaźnik do struktury obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1000">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1001">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1001">Return Values</span></span>

- <span data-ttu-id="aa55c-1002">**NX_SUCCESS** (0x00) obiekt licznika został pomyślnie pobrany.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1002">**NX_SUCCESS** (0x00) The counter object has be successfully retrieved.</span></span>
- <span data-ttu-id="aa55c-1003">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1003">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1004">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1004">Allowed From</span></span>

<span data-ttu-id="aa55c-1005">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1005">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1006">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1006">Example</span></span>

```c
/* Get the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object.  */
status =  nx_snmp_object_counter_get(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter_set"></a><span data-ttu-id="aa55c-1007">nx_snmp_object_counter_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-1007">nx_snmp_object_counter_set</span></span>
<span data-ttu-id="aa55c-1008">Ustaw obiekt licznika</span><span class="sxs-lookup"><span data-stu-id="aa55c-1008">Set counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1009">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1009">Prototype</span></span>

```c
UINT  nx_snmp_object_counter_set(VOID *destination_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1010">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1010">Description</span></span>

<span data-ttu-id="aa55c-1011">Ta usługa ustawia licznik na adres określony przez wskaźnik docelowy z wartością licznika w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1011">This service sets the counter at the address specified by the destination pointer with the counter value in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1012">Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1012">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1013">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1013">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1014">**destination_ptr** Wskaźnik do elementu docelowego licznika.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1014">**destination_ptr** Pointer to counter destination.</span></span>
- <span data-ttu-id="aa55c-1015">**object_data** Wskaźnik do struktury obiektu źródłowego licznika.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1015">**object_data** Pointer to counter source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1016">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1016">Return Values</span></span>

- <span data-ttu-id="aa55c-1017">**NX_SUCCESS** (0x00) obiekt licznika został pomyślnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1017">**NX_SUCCESS** (0x00) The counter object has be successfully set.</span></span>
- <span data-ttu-id="aa55c-1018">**NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1018">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="aa55c-1019">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1019">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1020">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1020">Allowed From</span></span>

<span data-ttu-id="aa55c-1021">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1021">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1022">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1022">Example</span></span>

```c
/* Set the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object with
   the counter object value contained in my_object.  */
status =  nx_snmp_object_counter_set(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   set. */
```

## <a name="nx_snmp_object_counter64_get"></a><span data-ttu-id="aa55c-1023">nx_snmp_object_counter64_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-1023">nx_snmp_object_counter64_get</span></span>
<span data-ttu-id="aa55c-1024">Pobierz 64-bitowy obiekt licznika</span><span class="sxs-lookup"><span data-stu-id="aa55c-1024">Get 64-bit counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1025">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1025">Prototype</span></span>

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1026">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1026">Description</span></span>

<span data-ttu-id="aa55c-1027">Ta usługa pobiera 64-bitowy obiekt licznika pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1027">This service retrieves the 64-bit counter object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1028">Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1028">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1029">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1029">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1030">**source_ptr** Wskaźnik do źródła licznika.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1030">**source_ptr** Pointer to counter source.</span></span>
- <span data-ttu-id="aa55c-1031">**object_data** Wskaźnik do struktury obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1031">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1032">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1032">Return Values</span></span>

- <span data-ttu-id="aa55c-1033">**NX_SUCCESS** (0x00) obiekt licznika został pomyślnie pobrany.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1033">**NX_SUCCESS** (0x00) The counter object has be successfully retrieved.</span></span>
- <span data-ttu-id="aa55c-1034">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1034">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1035">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1035">Allowed From</span></span>

<span data-ttu-id="aa55c-1036">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1036">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1037">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1037">Example</span></span>

```c
/* Get the value of my_64_bit_counter and place it into my_object
   for return.  */
status =  nx_snmp_object_counter64_get(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter64_set"></a><span data-ttu-id="aa55c-1038">nx_snmp_object_counter64_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-1038">nx_snmp_object_counter64_set</span></span>
<span data-ttu-id="aa55c-1039">Ustaw 64-bitowy obiekt licznika</span><span class="sxs-lookup"><span data-stu-id="aa55c-1039">Set 64-bit counter object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1040">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1040">Prototype</span></span>

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a><span data-ttu-id="aa55c-1041">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1041">Description</span></span>

<span data-ttu-id="aa55c-1042">Ta usługa ustawia 64-bitowy licznik na adres określony przez wskaźnik docelowy z wartością licznika w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1042">This service sets the 64-bit counter at the address specified by the destination pointer with the counter value in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1043">Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1043">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1044">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1044">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1045">**destination_ptr** Wskaźnik do elementu docelowego licznika.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1045">**destination_ptr** Pointer to counter destination.</span></span>
- <span data-ttu-id="aa55c-1046">**object_data** Wskaźnik do struktury obiektu źródłowego licznika.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1046">**object_data** Pointer to counter source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1047">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1047">Return Values</span></span>

- <span data-ttu-id="aa55c-1048">**NX_SUCCESS** (0x00) obiekt licznika został pomyślnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1048">**NX_SUCCESS** (0x00) The counter object has be successfully set.</span></span>
- <span data-ttu-id="aa55c-1049">**NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1049">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="aa55c-1050">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1050">**NX_PTR_ERROR** (0x07) Invalid input pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1051">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1051">Allowed From</span></span>

<span data-ttu-id="aa55c-1052">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1052">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1053">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1053">Example</span></span>

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a><span data-ttu-id="aa55c-1054">nx_snmp_object_end_of_mib</span><span class="sxs-lookup"><span data-stu-id="aa55c-1054">nx_snmp_object_end_of_mib</span></span>
<span data-ttu-id="aa55c-1055">Ustaw wartość końca MIB</span><span class="sxs-lookup"><span data-stu-id="aa55c-1055">Set end-of-mib value</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1056">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1056">Prototype</span></span>

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1057">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1057">Description</span></span>

<span data-ttu-id="aa55c-1058">Ta usługa tworzy obiekt sygnalizujący koniec MIB i jest zazwyczaj wywoływany z procedury wywołania zwrotnego GET lub GetNext aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1058">This service creates an object signaling the end of the MIB and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1059">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1059">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1060">**not_used_ptr** Wskaźnik nie jest używany — powinien być NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1060">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="aa55c-1061">**object_data** Wskaźnik do struktury obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1061">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1062">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1062">Return Values</span></span>

- <span data-ttu-id="aa55c-1063">**NX_SUCCESS** (0x00) obiekt końca bazy MIB został pomyślnie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1063">**NX_SUCCESS** (0x00) The end-of-mib object has be successfully built.</span></span>
- <span data-ttu-id="aa55c-1064">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1064">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1065">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1065">Allowed From</span></span>

<span data-ttu-id="aa55c-1066">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1066">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1067">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1067">Example</span></span>

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a><span data-ttu-id="aa55c-1068">nx_snmp_object_gauge_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-1068">nx_snmp_object_gauge_get</span></span>
<span data-ttu-id="aa55c-1069">Pobierz obiekt miernika</span><span class="sxs-lookup"><span data-stu-id="aa55c-1069">Get gauge object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1070">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1070">Prototype</span></span>

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1071">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1071">Description</span></span>

<span data-ttu-id="aa55c-1072">Ta usługa pobiera obiekt miernika pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1072">This service retrieves the gauge object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1073">Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1073">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1074">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1074">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1075">**source_ptr** Wskaźnik do źródła miernika.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1075">**source_ptr** Pointer to gauge source.</span></span>
- <span data-ttu-id="aa55c-1076">**object_data** Wskaźnik do struktury obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1076">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1077">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1077">Return Values</span></span>

- <span data-ttu-id="aa55c-1078">**NX_SUCCESS** (0x00) obiekt miernika został pomyślnie pobrany.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1078">**NX_SUCCESS** (0x00) The gauge object has be successfully retrieved.</span></span>
- <span data-ttu-id="aa55c-1079">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1079">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1080">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1080">Allowed From</span></span>

<span data-ttu-id="aa55c-1081">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1081">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1082">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1082">Example</span></span>

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a><span data-ttu-id="aa55c-1083">nx_snmp_object_gauge_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-1083">nx_snmp_object_gauge_set</span></span>
<span data-ttu-id="aa55c-1084">Ustaw obiekt miernika</span><span class="sxs-lookup"><span data-stu-id="aa55c-1084">Set gauge object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1085">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1085">Prototype</span></span>

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1086">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1086">Description</span></span>

<span data-ttu-id="aa55c-1087">Ta usługa ustawia miernik na adres określony przez wskaźnik docelowy z wartością miernika w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1087">This service sets the gauge at the address specified by the destination pointer with the gauge value in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1088">Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1088">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1089">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1089">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1090">**destination_ptr** Wskaźnik do miejsca docelowego miernika.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1090">**destination_ptr** Pointer to gauge destination.</span></span>
- <span data-ttu-id="aa55c-1091">**object_data** Wskaźnik do struktury obiektu źródłowego miernika.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1091">**object_data** Pointer to gauge source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1092">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1092">Return Values</span></span>

- <span data-ttu-id="aa55c-1093">**NX_SUCCESS** (0x00) obiekt miernika został pomyślnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1093">**NX_SUCCESS** (0x00) The gauge object has be successfully set.</span></span>
- <span data-ttu-id="aa55c-1094">**NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1094">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="aa55c-1095">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1095">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1096">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1096">Allowed From</span></span>

<span data-ttu-id="aa55c-1097">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1097">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1098">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1098">Example</span></span>

```c
/* Set the value of “my_gauge” from the gauge value in my_object.  */
status =  nx_snmp_object_gauge_set(&my_gauge, my_object);

/* If status is NX_SUCCESS, the my_gauge now contains the new gauge value. */
```

## <a name="nx_snmp_object_id_get"></a><span data-ttu-id="aa55c-1099">nx_snmp_object_id_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-1099">nx_snmp_object_id_get</span></span>
<span data-ttu-id="aa55c-1100">Pobierz identyfikator obiektu</span><span class="sxs-lookup"><span data-stu-id="aa55c-1100">Get object id</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1101">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1101">Prototype</span></span>

```c
UINT  nx_snmp_object_id_get(VOID *source_ptr, 
                            NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1102">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1102">Description</span></span>

<span data-ttu-id="aa55c-1103">Ta usługa Pobiera identyfikator obiektu (w notacji ASCII SIM) pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1103">This service retrieves the object ID (in ASCII SIM notation) at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1104">Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1104">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1105">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1105">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1106">**source_ptr** Wskaźnik do źródła identyfikatora obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1106">**source_ptr** Pointer to object ID source.</span></span>
- <span data-ttu-id="aa55c-1107">**object_data** Wskaźnik do struktury obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1107">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1108">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1108">Return Values</span></span>

- <span data-ttu-id="aa55c-1109">**NX_SUCCESS** (0X00) identyfikator obiektu został pomyślnie pobrany.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1109">**NX_SUCCESS** (0x00) The object ID has be successfully retrieved.</span></span>
- <span data-ttu-id="aa55c-1110">**NX_SNMP_ERROR** (0X100) Nieprawidłowa długość obiektu</span><span class="sxs-lookup"><span data-stu-id="aa55c-1110">**NX_SNMP_ERROR** (0x100) Invalid length of object</span></span>
- <span data-ttu-id="aa55c-1111">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1111">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1112">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1112">Allowed From</span></span>

<span data-ttu-id="aa55c-1113">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1113">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1114">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1114">Example</span></span>

```c
/* Get the value of sysObjectID(1.3.6.1.2.1.1.2.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_id_get(&sysObjectID, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysObjectID value. */
```

## <a name="nx_snmp_object_id_set"></a><span data-ttu-id="aa55c-1115">nx_snmp_object_id_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-1115">nx_snmp_object_id_set</span></span>
<span data-ttu-id="aa55c-1116">Ustaw identyfikator obiektu</span><span class="sxs-lookup"><span data-stu-id="aa55c-1116">Set object id</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1117">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1117">Prototype</span></span>

```c
UINT  nx_snmp_object_id_set(VOID *destination_ptr, 
                             NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1118">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1118">Description</span></span>

<span data-ttu-id="aa55c-1119">Ta usługa ustawia identyfikator obiektu (w notacji XML SIM) na adres określony przez wskaźnik docelowy z IDENTYFIKATORem obiektu w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1119">This service sets the object ID (in ASCII SIM notation) at the address specified by the destination pointer with the object ID in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1120">Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1120">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1121">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1121">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1122">**destination_ptr** Wskaźnik do obiektu docelowego o IDENTYFIKATORze.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1122">**destination_ptr** Pointer to object ID destination.</span></span>
- <span data-ttu-id="aa55c-1123">**object_data** Wskaźnik do struktury obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1123">**object_data** Pointer to object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1124">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1124">Return Values</span></span>

- <span data-ttu-id="aa55c-1125">**NX_SUCCESS** (0X00) identyfikator obiektu został pomyślnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1125">**NX_SUCCESS** (0x00) The object ID has been successfully set.</span></span>
- <span data-ttu-id="aa55c-1126">**NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1126">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="aa55c-1127">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1127">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1128">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1128">Allowed From</span></span>

<span data-ttu-id="aa55c-1129">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1129">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1130">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1130">Example</span></span>

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a><span data-ttu-id="aa55c-1131">nx_snmp_object_integer_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-1131">nx_snmp_object_integer_get</span></span>
<span data-ttu-id="aa55c-1132">Pobierz obiekt typu Integer</span><span class="sxs-lookup"><span data-stu-id="aa55c-1132">Get integer object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1133">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1133">Prototype</span></span>

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1134">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1134">Description</span></span>

<span data-ttu-id="aa55c-1135">Ta usługa pobiera obiekt liczby całkowitej na adres określony przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1135">This service retrieves the integer object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1136">Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1136">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1137">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1137">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1138">**source_ptr** Wskaźnik na źródło wartości całkowitej.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1138">**source_ptr** Pointer to integer source.</span></span>
- <span data-ttu-id="aa55c-1139">**object_data** Wskaźnik do struktury obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1139">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1140">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1140">Return Values</span></span>

- <span data-ttu-id="aa55c-1141">**NX_SUCCESS** (0x00) pomyślnie pobrano obiekt typu Integer.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1141">**NX_SUCCESS** (0x00) The integer object has been successfully retrieved.</span></span>
- <span data-ttu-id="aa55c-1142">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1142">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1143">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1143">Allowed From</span></span>

<span data-ttu-id="aa55c-1144">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1144">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1145">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1145">Example</span></span>

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a><span data-ttu-id="aa55c-1146">nx_snmp_object_integer_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-1146">nx_snmp_object_integer_set</span></span>
<span data-ttu-id="aa55c-1147">Ustaw obiekt liczb całkowitych</span><span class="sxs-lookup"><span data-stu-id="aa55c-1147">Set integer object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1148">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1148">Prototype</span></span>

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1149">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1149">Description</span></span>

<span data-ttu-id="aa55c-1150">Ta usługa ustawia liczbę całkowitą na adres określony przez wskaźnik docelowy za pomocą wartości całkowitej w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1150">This service sets the integer at the address specified by the destination pointer with the integer value in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1151">Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1151">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1152">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1152">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1153">**destination_ptr** Wskaźnik na miejsce docelowe liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1153">**destination_ptr** Pointer to integer destination.</span></span>
- <span data-ttu-id="aa55c-1154">**object_data** Wskaźnik do struktury obiektów źródłowych w postaci liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1154">**object_data** Pointer to integer source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1155">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1155">Return Values</span></span>

- <span data-ttu-id="aa55c-1156">**NX_SUCCESS** (0x00) pomyślnie ustawiono obiekt typu Integer.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1156">**NX_SUCCESS** (0x00) The integer object has been successfully set.</span></span>
- <span data-ttu-id="aa55c-1157">**NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1157">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="aa55c-1158">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1158">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1159">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1159">Allowed From</span></span>

<span data-ttu-id="aa55c-1160">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1160">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1161">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1161">Example</span></span>

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a><span data-ttu-id="aa55c-1162">nx_snmp_object_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-1162">nx_snmp_object_ip_address_get</span></span>
<span data-ttu-id="aa55c-1163">Pobierz obiekt adresu IP (tylko IPv4)</span><span class="sxs-lookup"><span data-stu-id="aa55c-1163">Get IP address object (IPv4 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-1164">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1164">Prototype</span></span>

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1165">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1165">Description</span></span>

<span data-ttu-id="aa55c-1166">Ta usługa pobiera obiekt adresu IP pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1166">This service retrieves the IP address object at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1167">Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1167">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1168">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1168">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1169">**source_ptr** Wskaźnik na źródło adresów IPv4.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1169">**source_ptr** Pointer to IPv4 address source.</span></span>
- <span data-ttu-id="aa55c-1170">**object_data** Wskaźnik do struktury obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1170">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1171">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1171">Return Values</span></span>

- <span data-ttu-id="aa55c-1172">**NX_SUCCESS** (0x00) obiekt adresu IP został pomyślnie pobrany.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1172">**NX_SUCCESS** (0x00) The IP address object has been successfully retrieved.</span></span>
- <span data-ttu-id="aa55c-1173">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1173">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1174">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1174">Allowed From</span></span>

<span data-ttu-id="aa55c-1175">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1175">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1176">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1176">Example</span></span>

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a><span data-ttu-id="aa55c-1177">nx_snmp_object_ipv6_address_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-1177">nx_snmp_object_ipv6_address_get</span></span>
<span data-ttu-id="aa55c-1178">Pobieranie obiektu adresu IP (tylko protokół IPv6)</span><span class="sxs-lookup"><span data-stu-id="aa55c-1178">Get IP address object (IPv6 only)</span></span>

### <a name="prototype"></a><span data-ttu-id="aa55c-1179">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1179">Prototype</span></span>

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1180">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1180">Description</span></span>

<span data-ttu-id="aa55c-1181">Ta usługa pobiera obiekt adresu IPv6 pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1181">This service retrieves the IPv6 address object at the address specified by the source pointer and places it in the NetX object data structure.</span></span>
<span data-ttu-id="aa55c-1182">Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1182">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1183">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1183">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1184">**source_ptr** Wskaźnik na źródło adresów IPv6.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1184">**source_ptr** Pointer to IPv6 address source.</span></span>
- <span data-ttu-id="aa55c-1185">**object_data** Wskaźnik do struktury obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1185">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1186">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1186">Return Values</span></span>

- <span data-ttu-id="aa55c-1187">**NX_SUCCESS** (0x00) obiekt adresu IP został pomyślnie pobrany.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1187">**NX_SUCCESS** (0x00) The IP address object has been successfully retrieved.</span></span>
- <span data-ttu-id="aa55c-1188">**NX_SNMP_ERROR_WRONGTYPE** (0X07) nieprawidłowy wejściowy kod obiektu SNMP</span><span class="sxs-lookup"><span data-stu-id="aa55c-1188">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Incorrect input SNMP object code</span></span>
- <span data-ttu-id="aa55c-1189">**NX_NOT_ENABLED** (0X14) protokół IPv6 nie jest włączony</span><span class="sxs-lookup"><span data-stu-id="aa55c-1189">**NX_NOT_ENABLED** (0x14) IPv6 not enabled</span></span>
- <span data-ttu-id="aa55c-1190">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1190">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1191">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1191">Allowed From</span></span>

<span data-ttu-id="aa55c-1192">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1192">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1193">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1193">Example</span></span>

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ipv6_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ip_address_set"></a><span data-ttu-id="aa55c-1194">nx_snmp_object_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-1194">nx_snmp_object_ip_address_set</span></span>
<span data-ttu-id="aa55c-1195">Ustawianie obiektu adresu IPv4</span><span class="sxs-lookup"><span data-stu-id="aa55c-1195">Set IPv4 address object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1196">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1196">Prototype</span></span>

```c
UINT  nx_snmp_object_ip_address_set(VOID *destination_ptr, 
                                    NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1197">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1197">Description</span></span>

<span data-ttu-id="aa55c-1198">Ta usługa ustawia adres IPv4 na adres określony przez wskaźnik docelowy przy użyciu adresu IP w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1198">This service sets the IPv4 address at the address specified by the destination pointer with the IP address in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1199">Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1199">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1200">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1200">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1201">**destination_ptr** Wskaźnik na adres IP, który ma zostać ustawiony.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1201">**destination_ptr** Pointer to IP address to set.</span></span>
- <span data-ttu-id="aa55c-1202">**object_data** Wskaźnik do struktury obiektów adresów IP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1202">**object_data** Pointer to IP address object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1203">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1203">Return Values</span></span>

- <span data-ttu-id="aa55c-1204">**NX_SUCCESS** (0x00) obiekt adresu IP został pomyślnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1204">**NX_SUCCESS** (0x00) The IP address object has been successfully set.</span></span>
- <span data-ttu-id="aa55c-1205">**NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1205">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="aa55c-1206">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1206">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1207">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1207">Allowed From</span></span>

<span data-ttu-id="aa55c-1208">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1208">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1209">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1209">Example</span></span>

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ip_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_ipv6_address_set"></a><span data-ttu-id="aa55c-1210">nx_snmp_object_ipv6_address_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-1210">nx_snmp_object_ipv6_address_set</span></span>
<span data-ttu-id="aa55c-1211">Ustawianie obiektu adresu IPv6</span><span class="sxs-lookup"><span data-stu-id="aa55c-1211">Set IPv6 address object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1212">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1212">Prototype</span></span>

```c
UINT  nx_snmp_object_ipv6_address_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA  
                                      *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1213">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1213">Description</span></span>

<span data-ttu-id="aa55c-1214">Ta usługa ustawia adres IPv6 pod adresem wskazanym przez wskaźnik docelowy przy użyciu adresu IP w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1214">This service sets the IPv6 address at the address specified by the destination pointer with the IP address in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1215">Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1215">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1216">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1216">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1217">**destination_ptr** Wskaźnik na adres IP, który ma zostać ustawiony.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1217">**destination_ptr** Pointer to IP address to set.</span></span>
- <span data-ttu-id="aa55c-1218">**object_data** Wskaźnik do struktury obiektów adresów IP.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1218">**object_data** Pointer to IP address object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1219">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1219">Return Values</span></span>

- <span data-ttu-id="aa55c-1220">**NX_SUCCESS** (0x00) adres IPv6 został pomyślnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1220">**NX_SUCCESS** (0x00) The IPv6 address has been successfully set.</span></span>
- <span data-ttu-id="aa55c-1221">**NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1221">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="aa55c-1222">**NX_NOT_ENABLED** (0X14) protokół IPv6 nie jest włączony</span><span class="sxs-lookup"><span data-stu-id="aa55c-1222">**NX_NOT_ENABLED** (0x14) IPv6 not enabled</span></span>
- <span data-ttu-id="aa55c-1223">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1223">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1224">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1224">Allowed From</span></span>

<span data-ttu-id="aa55c-1225">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1225">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1226">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1226">Example</span></span>

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a><span data-ttu-id="aa55c-1227">nx_snmp_object_no_instance</span><span class="sxs-lookup"><span data-stu-id="aa55c-1227">nx_snmp_object_no_instance</span></span>
<span data-ttu-id="aa55c-1228">Ustaw obiekt bez wystąpienia</span><span class="sxs-lookup"><span data-stu-id="aa55c-1228">Set no-instance object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1229">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1229">Prototype</span></span>

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1230">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1230">Description</span></span>

<span data-ttu-id="aa55c-1231">Ta usługa tworzy obiekt sygnalizujący, że nie ma żadnego wystąpienia określonego obiektu i jest zazwyczaj wywoływany z procedury wywołania zwrotnego GET lub GetNext Application.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1231">This service creates an object signaling that there was no instance of the specified object and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1232">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1232">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1233">**not_used_ptr** Wskaźnik nie jest używany — powinien być NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1233">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="aa55c-1234">**object_data** Wskaźnik do struktury obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1234">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1235">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1235">Return Values</span></span>

- <span data-ttu-id="aa55c-1236">**NX_SUCCESS** (0x00) obiekt bez wystąpienia został pomyślnie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1236">**NX_SUCCESS** (0x00) The no-instance object has been successfully built.</span></span>
- <span data-ttu-id="aa55c-1237">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1237">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1238">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1238">Allowed From</span></span>

<span data-ttu-id="aa55c-1239">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1239">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1240">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1240">Example</span></span>

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a><span data-ttu-id="aa55c-1241">nx_snmp_object_not_found</span><span class="sxs-lookup"><span data-stu-id="aa55c-1241">nx_snmp_object_not_found</span></span>
<span data-ttu-id="aa55c-1242">Nie znaleziono obiektu</span><span class="sxs-lookup"><span data-stu-id="aa55c-1242">Set not-found object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1243">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1243">Prototype</span></span>

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1244">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1244">Description</span></span>

<span data-ttu-id="aa55c-1245">Ta usługa tworzy obiekt sygnalizujący, że obiekt nie został odnaleziony i jest zazwyczaj wywoływany z procedury wywołania zwrotnego GET lub GetNext Application.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1245">This service creates an object signaling the object was not found and is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1246">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1246">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1247">**not_used_ptr** Wskaźnik nie jest używany — powinien być NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1247">**not_used_ptr** Pointer not used – should be NX_NULL.</span></span>
- <span data-ttu-id="aa55c-1248">**object_data** Wskaźnik do struktury obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1248">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1249">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1249">Return Values</span></span>

- <span data-ttu-id="aa55c-1250">**NX_SUCCESS** (0x00) obiekt, który nie został znaleziony, został pomyślnie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1250">**NX_SUCCESS** (0x00) The not-found object has been successfully built.</span></span>
- <span data-ttu-id="aa55c-1251">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1251">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1252">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1252">Allowed From</span></span>

<span data-ttu-id="aa55c-1253">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1253">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1254">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1254">Example</span></span>

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a><span data-ttu-id="aa55c-1255">nx_snmp_object_octet_string_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-1255">nx_snmp_object_octet_string_get</span></span>
<span data-ttu-id="aa55c-1256">Pobieranie obiektu ciągu oktetowego</span><span class="sxs-lookup"><span data-stu-id="aa55c-1256">Get octet string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1257">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1257">Prototype</span></span>

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a><span data-ttu-id="aa55c-1258">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1258">Description</span></span>

<span data-ttu-id="aa55c-1259">Ta usługa Pobiera ciąg oktetowy pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1259">This service retrieves the octet string at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1260">Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1260">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1261">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1261">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1262">**source_ptr** Wskaźnik na źródło ciągu oktetowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1262">**source_ptr** Pointer to octet string source.</span></span>
- <span data-ttu-id="aa55c-1263">**object_data** Wskaźnik do struktury obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1263">**object_data** Pointer to destination object structure.</span></span>
- <span data-ttu-id="aa55c-1264">**Długość** Liczba bajtów w ciągu oktetu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1264">**length** Number of bytes in octet string.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1265">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1265">Return Values</span></span>

- <span data-ttu-id="aa55c-1266">**NX_SUCCESS** (0x00) obiekt ciągu oktetowego został pomyślnie pobrany.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1266">**NX_SUCCESS** (0x00) The octet string object has been successfully retrieved.</span></span>
- <span data-ttu-id="aa55c-1267">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1267">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1268">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1268">Allowed From</span></span>

<span data-ttu-id="aa55c-1269">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1269">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1270">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1270">Example</span></span>

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a><span data-ttu-id="aa55c-1271">nx_snmp_object_octet_string_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-1271">nx_snmp_object_octet_string_set</span></span>
<span data-ttu-id="aa55c-1272">Ustawianie obiektu ciągu oktetowego</span><span class="sxs-lookup"><span data-stu-id="aa55c-1272">Set octet string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1273">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1273">Prototype</span></span>

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1274">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1274">Description</span></span>

<span data-ttu-id="aa55c-1275">Ta usługa ustawia ciąg oktetu na adres określony przez wskaźnik docelowy z ciągiem oktetu w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1275">This service sets the octet string at the address specified by the destination pointer with the octet string in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1276">Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1276">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1277">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1277">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1278">**destination_ptr** Wskaźnik na miejsce docelowe ciągu oktetowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1278">**destination_ptr** Pointer to octet string destination.</span></span>
- <span data-ttu-id="aa55c-1279">**object_data** Wskaźnik na strukturę obiektu źródłowego ciągu oktetowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1279">**object_data** Pointer to octet string source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1280">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1280">Return Values</span></span>

- <span data-ttu-id="aa55c-1281">**NX_SUCCESS** (0x00) obiekt ciągu oktetowego został pomyślnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1281">**NX_SUCCESS** (0x00) The octet string object has been successfully set.</span></span>
- <span data-ttu-id="aa55c-1282">**NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1282">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="aa55c-1283">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1283">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1284">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1284">Allowed From</span></span>

<span data-ttu-id="aa55c-1285">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1285">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1286">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1286">Example</span></span>

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   octet string in my_object.  */
status =  nx_snmp_object_octet_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new octet string. */
```

## <a name="nx_snmp_object_string_get"></a><span data-ttu-id="aa55c-1287">nx_snmp_object_string_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-1287">nx_snmp_object_string_get</span></span>
<span data-ttu-id="aa55c-1288">Pobierz obiekt ciągu ASCII</span><span class="sxs-lookup"><span data-stu-id="aa55c-1288">Get ASCII string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1289">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1289">Prototype</span></span>

```c
UINT  nx_snmp_object_string_get(VOID *source_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1290">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1290">Description</span></span>

<span data-ttu-id="aa55c-1291">Ta usługa Pobiera ciąg ASCII pod adresem określonym przez wskaźnik źródła i umieszcza go w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1291">This service retrieves the ASCII string at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1292">Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1292">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1293">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1293">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1294">**source_ptr** Wskaźnik do źródła ciągu ASCII.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1294">**source_ptr** Pointer to ASCII string source.</span></span>
- <span data-ttu-id="aa55c-1295">**object_data** Wskaźnik do struktury obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1295">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1296">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1296">Return Values</span></span>

- <span data-ttu-id="aa55c-1297">**NX_SUCCESS** (0x00) obiekt ciągu ASCII został pomyślnie pobrany.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1297">**NX_SUCCESS** (0x00) The ASCII string object has been successfully retrieved.</span></span>
- <span data-ttu-id="aa55c-1298">Ciąg **NX_SNMP_ERROR** (0x100) jest zbyt duży</span><span class="sxs-lookup"><span data-stu-id="aa55c-1298">**NX_SNMP_ERROR** (0x100) String is too big</span></span>  
- <span data-ttu-id="aa55c-1299">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1299">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1300">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1300">Allowed From</span></span>

<span data-ttu-id="aa55c-1301">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1301">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1302">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1302">Example</span></span>

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a><span data-ttu-id="aa55c-1303">nx_snmp_object_string_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-1303">nx_snmp_object_string_set</span></span>
<span data-ttu-id="aa55c-1304">Ustaw obiekt ciągu ASCII</span><span class="sxs-lookup"><span data-stu-id="aa55c-1304">Set ASCII string object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1305">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1305">Prototype</span></span>

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1306">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1306">Description</span></span>

<span data-ttu-id="aa55c-1307">Ta usługa ustawia ciąg ASCII na adres określony przez wskaźnik docelowy z ciągiem ASCII w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1307">This service sets the ASCII string at the address specified by the destination pointer with the ASCII string in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1308">Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1308">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1309">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1309">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1310">**destination_ptr** Wskaźnik do miejsca docelowego ciągu ASCII.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1310">**destination_ptr** Pointer to ASCII string destination.</span></span>
- <span data-ttu-id="aa55c-1311">**object_data** Wskaźnik do struktury obiektu źródłowego ciągu ASCII.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1311">**object_data** Pointer to ASCII string source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1312">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1312">Return Values</span></span>

- <span data-ttu-id="aa55c-1313">**NX_SUCCESS** (0x00) obiekt ciągu ASCII został pomyślnie ustawiony.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1313">**NX_SUCCESS** (0x00) The ASCII string object has been successfully set.</span></span>
- <span data-ttu-id="aa55c-1314">Ciąg **NX_SNMP_ERROR** (0x100) jest zbyt duży.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1314">**NX_SNMP_ERROR** (0x100) String too large.</span></span>
- <span data-ttu-id="aa55c-1315">**NX_SNMP_ERROR_BADVALUE** (0X03) nieprawidłowy znak w ciągu</span><span class="sxs-lookup"><span data-stu-id="aa55c-1315">**NX_SNMP_ERROR_BADVALUE** (0x03) Invalid character in string</span></span>
- <span data-ttu-id="aa55c-1316">**NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1316">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="aa55c-1317">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1317">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1318">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1318">Allowed From</span></span>

<span data-ttu-id="aa55c-1319">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1319">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1320">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1320">Example</span></span>

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   ASCII string in my_object.  */
status =  nx_snmp_object_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new ASCII string. */
```

## <a name="nx_snmp_object_timetics_get"></a><span data-ttu-id="aa55c-1321">nx_snmp_object_timetics_get</span><span class="sxs-lookup"><span data-stu-id="aa55c-1321">nx_snmp_object_timetics_get</span></span>
<span data-ttu-id="aa55c-1322">Pobierz obiekt timetics</span><span class="sxs-lookup"><span data-stu-id="aa55c-1322">Get timetics object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1323">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1323">Prototype</span></span>

```c
UINT  nx_snmp_object_timetics_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1324">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1324">Description</span></span>

<span data-ttu-id="aa55c-1325">Ta usługa pobiera timetics pod adresem określonym przez wskaźnik źródła i umieszcza je w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1325">This service retrieves the timetics at the address specified by the source pointer and places it in the NetX object data structure.</span></span> <span data-ttu-id="aa55c-1326">Ta procedura jest zwykle wywoływana z procedury wywołania zwrotnego GET lub GetNext aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1326">This routine is typically called from the GET or GETNEXT application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1327">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1327">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1328">**source_ptr** Wskaźnik do źródła timetics.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1328">**source_ptr** Pointer to timetics source.</span></span>
- <span data-ttu-id="aa55c-1329">**object_data** Wskaźnik do struktury obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1329">**object_data** Pointer to destination object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1330">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1330">Return Values</span></span>

- <span data-ttu-id="aa55c-1331">**NX_SUCCESS** (0x00) pomyślnie pobrano obiekt timetics.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1331">**NX_SUCCESS** (0x00) The timetics object has been successfully retrieved.</span></span>
- <span data-ttu-id="aa55c-1332">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1332">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1333">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1333">Allowed From</span></span>

<span data-ttu-id="aa55c-1334">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1334">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1335">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1335">Example</span></span>

```c
/* Get the value of the sysUpTime (1.3.6.1.2.1.1.3.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_timetics_get(sysUpTime, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysUpTime value. */
```

## <a name="nx_snmp_object_timetics_set"></a><span data-ttu-id="aa55c-1336">nx_snmp_object_timetics_set</span><span class="sxs-lookup"><span data-stu-id="aa55c-1336">nx_snmp_object_timetics_set</span></span>
<span data-ttu-id="aa55c-1337">Ustaw obiekt timetics</span><span class="sxs-lookup"><span data-stu-id="aa55c-1337">Set timetics object</span></span> 

### <a name="prototype"></a><span data-ttu-id="aa55c-1338">Prototype</span><span class="sxs-lookup"><span data-stu-id="aa55c-1338">Prototype</span></span>

```c
UINT  nx_snmp_object_timetics_set(VOID *destination_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a><span data-ttu-id="aa55c-1339">Opis</span><span class="sxs-lookup"><span data-stu-id="aa55c-1339">Description</span></span>

<span data-ttu-id="aa55c-1340">Ta usługa ustawia zmienną timetics na adres określony przez wskaźnik docelowy z timetics w strukturze danych obiektów NetX.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1340">This service sets the timetics variable at the address specified by the destination pointer with the timetics in the NetX object data structure.</span></span>
<span data-ttu-id="aa55c-1341">Ta procedura jest zazwyczaj wywoływana z procedury wywołania zwrotnego ustawiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1341">This routine is typically called from the SET application callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa55c-1342">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="aa55c-1342">Input Parameters</span></span>

- <span data-ttu-id="aa55c-1343">**destination_ptr** Wskaźnik do lokalizacji docelowej timetics.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1343">**destination_ptr** Pointer to timetics destination.</span></span>
- <span data-ttu-id="aa55c-1344">**object_data** Wskaźnik do timetics struktury obiektów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1344">**object_data** Pointer to timetics source object structure.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa55c-1345">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="aa55c-1345">Return Values</span></span>

- <span data-ttu-id="aa55c-1346">**NX_SUCCESS** (0x00) pomyślnie ustawiono obiekt timetics.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1346">**NX_SUCCESS** (0x00) The timetics object has been successfully set.</span></span>
- <span data-ttu-id="aa55c-1347">**NX_SNMP_ERROR_WRONGTYPE** (0X07) Nieprawidłowy typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="aa55c-1347">**NX_SNMP_ERROR_WRONGTYPE** (0x07) Invalid object type.</span></span>
- <span data-ttu-id="aa55c-1348">**NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy</span><span class="sxs-lookup"><span data-stu-id="aa55c-1348">**NX_PTR_ERROR** (0x07) Invalid input pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa55c-1349">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="aa55c-1349">Allowed From</span></span>

<span data-ttu-id="aa55c-1350">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="aa55c-1350">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa55c-1351">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa55c-1351">Example</span></span>

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```